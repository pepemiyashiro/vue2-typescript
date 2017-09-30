<template>
  <div id="app">
    <div id="vue-love">
      <img src="./assets/logo.png">
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style lang="scss">
  @import './assets/scss/global/global';
</style>
