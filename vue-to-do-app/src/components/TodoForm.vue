<template>
  <div class="main">
    <input type="text" class="new-todo" placeholder="What needs to be done?" v-model="newTodo">
    <ul class="todo-list">
      <li v-for="todo in todos" :key="todo.id" class="view">
        <input type="checkbox" class="toggle">
        <label>{{ todo.title }}</label>
        <button type="button" class="destroy"></button>
      </li>
    </ul>
  </div>
</template>

<script>
import TaskList from "./TaskList";
export default {
  name: 'todo-form',
  components: {TaskList},
  data () {
    return {
      newTodo: '',
      todos: [
        {
          'id': 1,
          'title': 'Do some shores',
          'completed': false,
        },
        {
          'id': 2,
          'title': 'Check out codewars',
          'completed': true,
        },
        {
          'id': 3,
          'title': 'Finish this html+css but in vue way',
          'completed': false,
        },
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped src="@/styles/style.css">

</style>
