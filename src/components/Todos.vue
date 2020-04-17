<template>
  <div>
    <h1>TODO</h1>
    <form @submit="addTodo">
      <input type="text" v-model="title" name="title" placeholder="put your text ..." />
      <input type="submit" value="Submit" />
    </form>
    <div v-bind:key="todo.id" v-for="todo in _todos">
      <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem";
import { uuid } from "vue-uuid";

export default {
  name: "Todos",

  components: {
    TodoItem
  },

  props: ["_todos"],

  methods: {
    addTodo: function(event) {
      event.preventDefault();
      const nTodo = {
        id: uuid.v4(),
        title: this.title,
        completed: false
      };
      // emit add event to parent
      this.$emit("add-todo", nTodo);
      this.title = '';
    }
  },

  data: function() {
    return {
      title: ""
    };
  }
};
</script>

<style scoped>
</style>