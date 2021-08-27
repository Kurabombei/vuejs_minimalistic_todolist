<template>
  <ul class="todo-list">
    <li v-for="todo in todos" :key="todo.id" class="view">
      <input type="checkbox" class="toggle">
      <label>{{ todo.title }}</label>
      <button type="button" class="destroy"></button>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'task-list',
  props: {
    todos: Array,
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
