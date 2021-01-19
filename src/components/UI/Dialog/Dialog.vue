<template>
    <div>
        <div class="dialog" :class="{'show': show}">
            <template v-for="(icon, index) in dialogIcons">
                <app-dialog-item 
                    :key="icon.name" 
                    :name="icon.name" 
                    :icon="icon.icon" 
                    iconOnly 
                    iconSize="30px" 
                    itemSize="100px" 
                    :show="show"
                    :animationDelay="(index + 1) * 0.15"/>
            </template>
        </div>
        <app-backdrop :class="{'show': show}" @click="closeDialog"/>
    </div>
    
    
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import DialogItem from './DialogItem.vue';
import DialogIcon from './DialogIcon';
import Backdrop from '../Backdrop/Backdrop.vue';

@Component({
    components: {
        appDialogItem: DialogItem,
        appBackdrop: Backdrop
    }
})
export default class Dialog extends Vue {

    @Prop({required: true}) public dialogIcons!: DialogIcon[];
    @Prop({default: false}) public show!: boolean;


    closeDialog() {   
        this.$emit('onClose');
    }

}
</script>

<style lang="scss" scoped>
.dialog {
    display: flex;
    flex-flow: column;
    justify-content: space-evenly;
    align-items: center;
    height: 100%;
    width: 100%;
    position: fixed;
    top: 0;
    left: 0;
    opacity: 0;
    z-index: -1;
    pointer-events: none;

    &.show {
        opacity: 1;
        z-index: 100;
    }

    @include sm {
        flex-flow: row;
    }


}
</style>