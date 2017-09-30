<template>
  <div class="hello">
    <h1>{{ fullMessage }}</h1>
    <h2>Essential <em>Links</em></h2>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue'
  import Component from 'vue-class-component'

  @Component({})
  export default class Hello extends Vue {
    name: string = 'hello';

    get fullMessage() {
      return `Welcome to Vue 2 with Typescript`;
    }
  }
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
  @import '../assets/scss/global/global';
</style>
