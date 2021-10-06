<template>
  <footer class="footer">
    <span class="todo-count">
			<strong> {{ completedCount }} completed</strong>, {{ uncompletedCount }} left
		</span>
    <ul class="filters">
      <li><button class="footer__button" :class="{ active: filter === 'all'}" @click="$emit('filter-changed', 'all')">All</button></li>
      <li><button class="footer__button" :class="{ active: filter === 'active'}" @click="$emit('filter-changed', 'active')">Active</button></li>
      <li><button class="footer__button" :class="{ active: filter === 'completed'}" @click="$emit('filter-changed', 'completed')">Completed</button></li>
    </ul>
    <button v-if="completedCount > 0" class="clear-completed" @click="$emit('remove-completed')">Clear completed</button>
  </footer>
</template>

<script>
export default {
  name: "TodoFooter",
  props: {
    numberOfTodos: {type: Number},
    uncompletedCount: {type: Number},
    filter: {type: String},
  },
  computed: {
    completedCount() {
      return this.numberOfTodos - this.uncompletedCount;
    }
  }
}
</script>

<style scoped>

</style>
