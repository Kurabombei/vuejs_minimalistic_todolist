<template>
  <div  class="todoapp">
    <header class="header">
      <h1>todos</h1>
    </header>
    <todo-form></todo-form>
  </div>
</template>

<script>
import TodoForm from './components/TodoForm'
import TaskList from './components/TaskList'

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
