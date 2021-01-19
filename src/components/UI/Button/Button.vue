<template>
    <div class="button" @click="action">
        <i class="fas" :class="icon"></i>
    </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator';

@Component
export default class Button extends Vue {

    @Prop({default: ''}) public icon!: string;

    action() {
        this.$emit('action');
    }

}
</script>

<style lang="scss" scoped>
.button {
    height: 80px;
    width: 80px;
    position: fixed;
    bottom: 0;
    right: 0;
    z-index: 98;

    & > i {
        color: rgba(255, 255, 255, 1);
        font-size: 30px;
        
    }

    display: flex;
    align-items: center;
    justify-content: center;
    background-color: rgba(245, 160, 50, 1);
    height: 80px;
    width: 80px;
    border-radius: 40px;
    position: absolute;
    bottom: 10px;
    right: 10px;
    cursor: pointer;

    &:hover, &:active {
        background-color: rgb(250, 195, 124);
    }

}

</style>