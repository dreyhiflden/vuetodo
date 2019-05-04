<template>
  <div id="app">
    <TodoList/>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'

export default {
  name: 'app',
  components: {
    TodoList
  }
}
</script>

<style lang="scss">
  body {
    background: #9a9eb2;
    background: linear-gradient(to bottom, #9a9eb2 0%,#535668 100%);
    height: 100vh;
  }

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  margin: 40px auto 0 auto;
  width: 400px;
  padding: 20px;
  background: linear-gradient(to bottom, #515362 0%,#4b4d5c 100%);
}
</style>
