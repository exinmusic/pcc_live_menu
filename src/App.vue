<template>
  <div id="app">
    <HelloWorld msg='test' secret='oh cool'/>
  </div>
</template>

<script>

import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>

</style>
