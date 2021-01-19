<template>
    <div>
        <app-dialog :show="showDialog" :dialogIcons="dialogIcons" @onClose="closeModal"/>
        <app-button v-if="!showDialog" icon="fa-plus" @action="openModal"/>
        <app-button v-else icon="fa-times" @action="closeModal"/>
    </div>
</template>

<script lang="ts">
import {Component, Vue} from 'vue-property-decorator';
import Button from '../UI/Button/Button.vue';
import Dialog from '../UI/Dialog/Dialog.vue';
import DialogIcon from '../UI/Dialog/DialogIcon';

@Component({
    components: {
        appButton: Button,
        appDialog: Dialog
    }})
export default class Layout extends Vue {

    public showDialog = false;
    public dialogIcons: DialogIcon[] = [];

    created() {
        this.dialogIcons = [new DialogIcon('Home', 'fa-home'), new DialogIcon('Post', 'fa-edit'), new DialogIcon('Reports', 'fa-file-alt')];
    }

    openModal() {
        this.showDialog = true;
    }

    closeModal() {
        this.showDialog = false;
    }

}
</script>

<style lang="scss" scoped>

</style>