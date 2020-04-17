<template>
  <div id="app">
    <Todos v-bind:_todos="todos" v-on:del-todo="deleteTodo" v-on:add-todo="addTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos";

export default {
  name: "App",

  components: {
    Todos
  },

  methods: {
    deleteTodo: function(id) {
      this.todos = this.todos.filter(todo => todo.id != id);
    },
    addTodo: function(nTodo) {
      this.todos = [...this.todos, nTodo];
    }
  },

  data() {
    return {
      todos: []
    };
  }
};
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