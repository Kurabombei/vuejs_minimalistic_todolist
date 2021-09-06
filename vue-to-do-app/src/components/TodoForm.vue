<template>
  <div class="main">
    <input type="text" class="new-todo" placeholder="What needs to be done?" v-model="newTodo" v-on:keyup.enter="addTodo">
    <todo-list v-bind:todos="todos" @onDelete="onDelete"/>
    <todo-footer></todo-footer>
  </div>
</template>

<script>
import TodoList from "./TodoList";
import uniqueId from 'lodash.uniqueid';
import TodoFooter from "./TodoFooter";
export default {
  name: 'todo-form',
  components: {TodoFooter, TodoList},
  data () {
    return {
      newTodo: '',
      idForTodo: uniqueId('todo-'),
      todos: [
        {
          'id': uniqueId('todo-'),
          'title': 'Do some shores',
          'completed': false,
        },
        {
          'id': uniqueId('todo-'),
          'title': 'Check out codewars',
          'completed': true,
        },
        {
          'id': uniqueId('todo-'),
          'title': 'Finish this html+css but in vue way',
          'completed': false,
        },
      ],
      methods: {
        addTodo() {
          if(this.newTodo.trim().length == 0) {
            return
          }

          console.log("added a new todo with text");
          // this.todos.push({
          //   id: this.idForTodo,
          //   title: this.newTodo,
          //   completed: false,
          // })

          this.newTodo = ''
          this.idForTodo = uniqueId('todo-')
        },
        onDelete(id) {
          console.log("deleted");
          this.todos = this.todos.filter( t => t.id !== id)
        }
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style src="@/styles/style.css">

</style>
