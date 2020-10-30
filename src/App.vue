<template>
  <div id="app">
    <todolist list-name="My to-dos"/>
  </div>
</template>

<script>
import Todolist from "./components/Todolist.vue"

export default {
  name: 'App',
  components: {
    Todolist
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
