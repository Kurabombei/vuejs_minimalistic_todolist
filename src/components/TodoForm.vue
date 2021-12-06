<template>
  <div class="main">

    <input
      type="text"
      class="new-todo"
      placeholder="What needs to be done?"
      v-model="newTodo"
      v-on:keyup.enter="onAddTodo">
    <todo-list v-bind:todos="todosFiltered" v-on:deleteTodo="onDeleteTodo"/>
    <todo-footer
      v-bind:filter="filter"
      v-bind:uncompletedCount="remaining"
      v-bind:numberOfTodos="todos.length"
      v-on:remove-completed="onRemoveCompleted"
      v-on:filter-changed="onFilterChange" />
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
      editTodo: null,
      filter: 'all',

      todos: [
        {
          'id': uniqueId('todo-'),
          'title': 'Do some shores',
          'completed': false,
          'editing': false,
        },
        {
          'id': uniqueId('todo-'),
          'title': 'Check out codewars',
          'completed': true,
          'editing': false,
        },
        {
          'id': uniqueId('todo-'),
          'title': 'Finish this html+css but in vue way',
          'completed': false,
          'editing': false,
        },
      ],
    }
  },
  methods: {
    onAddTodo:function(){
      let newTodoText = this.newTodo && this.newTodo.trim();
      if(!newTodoText){
        return;
      }
      this.todos.push({id: uniqueId('todo-'),title: newTodoText, completed: false, editing: false});
      this.newTodo = '';
    },
    onRemoveCompleted:function(){
      this.todos = this.todos.filter((todo) => !todo.completed);
    },
    onDeleteTodo:function(id){
      this.todos = this.todos.filter( t => t.id !== id);
    },
    onFilterChange: function(filterText){
      this.filter = filterText;
    }
  },
  computed: {
    remaining() {
      return this.todos.filter( todo => !todo.completed).length;
    },
    todosFiltered() {
      if(this.filter === 'all'){
        return this.todos;
      } else if(this.filter === 'active') {
        return this.todos.filter(todo => !todo.completed);
      } else if (this.filter == 'completed') {
        return this.todos.filter(todo => todo.completed);
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style src="@/styles/style.css">

</style>
