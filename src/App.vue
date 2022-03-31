<template>
  <Header />
  <TodoList />
</template>

<script>
import Header from './components/Header.vue'
import TodoList from './components/TodoList.vue'

export default {
  name: 'App',
  components: {
    Header,
    TodoList,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
