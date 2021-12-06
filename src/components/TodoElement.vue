<template>
  <div class="view">
    <input type="checkbox" class="toggle" v-model="todo.completed"/>
    <label class="todo-element__left">
      <div
        :class="{ completed : todo.completed }"
        v-if="!todo.editing"
        v-on:dblclick="onEditTodo(todo)">
        {{ todo.title }}
      </div>
      <input
        class="edit"
        type="text"
        v-else
        v-model="todo.title"
        @blur="onDoneEdit(todo)"
        @keyup.enter="onDoneEdit(todo)"
        @keyup.esc="onCancelEdit(todo)"
        v-focus>
    </label>
    <button type="button" class="destroy" v-on:click="$emit('delete-todo', todo.id)"></button>
  </div>
</template>

<script>
export default {
  name: "todo-element",
  props: ['todo'],
  data() {
    return {
      isEdited: this.todo.editing,
      isCompleted : this.todo.completed,
      beforeEditCache: '',
    }
  },
  directives: {
    focus: {
      inserted: function(el) {
        el.focus();
      }
    }
  },
  methods: {
    onEditTodo:function(todo){
      todo.editing = true;
      this.beforeEditCache = todo.title;
      this.editedTodo = todo;
    },
    onDoneEdit:function(todo){
      if(!this.editedTodo){
        return;
      }
      todo.editing = false;
      this.editedTodo = null;
      todo.title = todo.title.trim();
      if(!todo.title){
        this.$emit('delete-todo', todo.id);
      }
    },
    onCancelEdit:function(todo){
      this.editedTodo = null;
      todo.title = this.beforeEditCache;
      todo.editing = false;
    },
  }
}
</script>

<style scoped>

</style>
