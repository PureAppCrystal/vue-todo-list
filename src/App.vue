<template>
  <div id="app">
    <TodoApp/>
  </div>
</template>

<script>

import TodoApp from './components/TodoApp.vue'
export default {
  name: 'app',
  components: {
    TodoApp,
  }
}
</script>

<style>
html {
  height:100%;
}

body {
  height:100%;
}

#app {
  width:100%;
  height:100%;
  display: flex;
  justify-content: center;
  /* align-items: center; */
}
</style>
