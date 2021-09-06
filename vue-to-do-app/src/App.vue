<template>
  <div  class="centered">
    <div  class="todoapp">
        <h1>todos</h1>
      <todo-form></todo-form>
    </div>
  </div>
</template>

<script>
import TodoForm from './components/TodoForm'
import TaskList from './components/TodoList'

export default {
  name: 'App',
  components: {
    TodoForm,
    TaskList,

  }
}
</script>

<style scoped src="@/styles/style.css">
</style>
