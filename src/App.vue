<template>
  <div id="app">
    <Converter />
  </div>
</template>

<script>
import Converter from './components/Converter.vue'

export default {
  name: 'app',
  components: {
    Converter
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100vh;
}
</style>
