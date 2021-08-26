<template>
  <div>
    <input type="text" class="new-todo" placeholder="What needs to be done?">
  </div>
  <main>
    <task-list></task-list>
  </main>
</template>

<script>
export default {
  name: 'todo-form',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
