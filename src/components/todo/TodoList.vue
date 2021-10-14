<template>
  <i-container class="_margin-top-2">
    <i-column>
      <TodoInput @add-todo-event="addTodo" />
    </i-column>
    <div v-if="!todos.length">
      <i-row>
        <i-column xs="12">
          <p class="_text-center">Empty</p>
        </i-column>
      </i-row>
    </div>
    <div v-else>
      <i-row>
        <i-column xs="12">
          <i-list-group size="sm">
            <i-list-group-item v-for="todo in todos" :key="todo.id">
              <TodoItem :todo="todo" @delete-todo-event="removeTodo" />
            </i-list-group-item>
          </i-list-group>
        </i-column>
      </i-row>
    </div>
  </i-container>
</template>

<script>
export default {
  name: "TodoList",
  components: {
    TodoInput: () => import("./TodoInput.vue"),
    TodoItem: () => import("./TodoItem.vue"),
  },

  data() {
    return {
      todos: [],
    };
  },

  methods: {
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    },

    removeTodo(todoId) {
      return (this.todos = this.todos.filter((todo) => todo.id !== todoId));
    },
  },
};
</script>
