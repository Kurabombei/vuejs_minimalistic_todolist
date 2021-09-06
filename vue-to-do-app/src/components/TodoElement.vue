<template>
  <div>
    <input type="checkbox" class="toggle">
    <label>{{ title }}</label>
    <button type="button" class="destroy" @click="onDelete(id)"></button>
  </div>
</template>

<script>
export default {
  name: "todo-element",
  props: {
    title: {required: true, type: String},
    completed: {default: false, type: Boolean},
    id: {required: true, type: String}
  },
  data() {
    return {
      isCompleted : this.completed,
    }
  },

}
</script>

<style scoped>

</style>
