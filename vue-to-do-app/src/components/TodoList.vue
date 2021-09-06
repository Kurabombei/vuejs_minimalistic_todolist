<template>
  <ul class="todo-list">
    <li v-for="todo in todos" :key="todo.id" class="view">
      <todo-element
        :title="todo.title"
        :completed="todo.done"
        :id="todo.id"
        @onDelete="onDelete"
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
    onDelete(id) {
      this.$emit('onDelete', id)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
