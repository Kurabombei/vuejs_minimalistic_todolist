<template>
  <ul class="todo-list">
    <li v-for="todo in todos" :key="todo.id">
      <todo-element
        :todo="todo"
        v-on:delete-todo="onDeleteTodo"
      ></todo-element>
    </li>
  </ul>
</template>

<script>
import TodoElement from "./TodoElement";
export default {
  name: 'todo-list',
  components: {TodoElement},
  props: {
    todos: Array,
  },
  methods:{
    onDeleteTodo(id) {
      this.$emit('deleteTodo', id)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
