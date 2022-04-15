<template>
  <div id="app">
    <HelloWorld />
    <HelloWorld2 />
  </div>
</template>

<script>
import HelloWorld from './components/FormDemo.vue'
import HelloWorld2 from './components/FormDemo2.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    HelloWorld2
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
}
</style>
