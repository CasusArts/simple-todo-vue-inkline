<template>
  <i-row>
    <i-column sx="2">
      <i-checkbox v-model="todo.isDone" @check="setIsDone"></i-checkbox>
      <span :class="{ 'is-done': todo.isDone }">{{ todo.text }}</span>
      <i-button @click="$emit('delete-todo-event', todo.id)" class="_float-right">
        <i-icon icon="times" size="sm" />
      </i-button>
    </i-column>
  </i-row>
</template>

<script>
export default {
  name: "TodoItem",
  data() {
    return {};
  },

  props: {
    todo: {
      id: Number,
      text: String,
      isDone: Boolean,
    },
  },

  methods: {
    setIsDone() {
      this.todo.isDone = !this.todo.isDone;
    },
  },
};
</script>

<style scoped>
.is-done {
  text-decoration: line-through;
}
</style>
