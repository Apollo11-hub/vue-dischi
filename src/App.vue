<template>
  <div>
    <header-layout></header-layout>
    <main-layout></main-layout>
  </div>
</template>

<script>
import HeaderLayout from './components/HeaderLayout.vue'
import MainLayout from './components/MainLayout.vue'


export default {
  name: 'App',
  components: {
    HeaderLayout,
    MainLayout
  }
}
</script>

<style lang="scss">
@import './assets/style/general';
@import './assets/style/utilities';

</style>
