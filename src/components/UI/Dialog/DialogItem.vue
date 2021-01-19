<template>
    <div 
        class="icon item" 
        :class="{'show': show}" 
        :style="'width: ' + itemSize + '; height: ' + itemSize + '; transition-delay: ' + animationDelay + 's'">
        <i 
           v-if="icon" 
           class="fa" 
           :class="icon" 
           :style="'font-size: ' + iconSize"/>
        <span v-if="!iconOnly">{{name}}</span>
    </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class DialogItem extends Vue {

    @Prop({default: ''}) public name!: string;
    @Prop({default: ''}) public icon!: string;
    @Prop({default: '1.2rem'}) public iconSize!: string;
    @Prop({default: '80px'}) public itemSize!: string;
    @Prop({type: Boolean}) public iconOnly!: boolean;
    @Prop({default: 'false'}) public show!: boolean;
    @Prop({default: '0'}) public animationDelay!: string;

}
</script>

<style lang="scss" scoped>
.item {
    display: flex;
    flex-flow: row;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    background-color: rgba(245, 160, 50, 1);
    color: #EEE;
    cursor: pointer;
    z-index: 110;
    pointer-events: all;

    &:hover, &:active {
        color: #333;
        background-color: rgb(250, 195, 124);
    }

    &.icon {
        transform: scale(0);
    }

    &.icon.show {
        transform: scale(1);
        transition: transform 0.5s;
    }

}
</style>