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
    min-height: 100vh;
  }

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #fff;
  margin: 40px auto 0 auto;
  width: 600px;
  padding: 20px;
  border-radius: 5px;
  background: linear-gradient(145deg, #545567 0%,#2a2a36 100%);;
}
</style>
