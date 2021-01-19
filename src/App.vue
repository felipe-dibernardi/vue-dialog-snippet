<template>
  <div id="app">
    <Layout/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Layout from './components/Layout/Layout.vue';

@Component({
  components: {
    Layout,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
</style>
