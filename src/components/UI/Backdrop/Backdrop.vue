<template>
    <div class="backdrop" :class="{'show': show}" @click="action"></div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class Backdrop extends Vue {

    @Prop({default: false}) public show!: boolean;

    action() {
        this.$emit('click');   
    }

}
</script>

<style lang="scss" scoped>
.backdrop {
    width: 100%;
    height: 100vh;
    background-color: rgba(0, 0, 0, 0.60);
    position: fixed;
    top: 0;
    left: 0;
    opacity: 0;
    z-index: -1;

    &.show {
        opacity: 1;
        z-index: 1;
    }
}
</style>