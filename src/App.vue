<template>
  <VList msg="Welcome to Your Vue.js App"/>
</template>

<script>
import VList from './components/VList.vue'

export default {
  name: 'App',
  components: {
    VList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
