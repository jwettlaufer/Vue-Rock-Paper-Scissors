<template>
  <div id="app">
    <Rps/>
  </div>
</template>

<script>
import Rps from './components/Rps.vue'

export default {
  name: 'App',
  components: {
    Rps
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
  margin-top: 60px;
  background: black;
}
</style>
