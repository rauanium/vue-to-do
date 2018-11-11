<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <TaskComp></TaskComp>
  </div>
</template>

<script>
import TaskComp from './components/TaskComp.vue'

export default {
  name: 'app',
  components: {
    TaskComp
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  text-align: center;
  color: #1a0841;
  margin-top: 60px;
}
</style>
