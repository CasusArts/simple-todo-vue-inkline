<template>
  <i-container>
    <i-row>
      <i-form @submit="addTodo" class="_margin-bottom-1">
        <i-input
          v-model="text"
          name="text"
          class="_display-inline-block _margin-right-1"
          size="md"
        />
        <i-button class="_display-inline-block">
          Add
        </i-button>
      </i-form>
    </i-row>
  </i-container>
</template>

<script>
import { v4 as uuidv4 } from "uuid";

export default {
  name: "Input",
  data() {
    return {
      text: "",
    };
  },
  methods: {
    addTodo(e) {
      if (this.text.length > 0) {
        e.preventDefault();

        const newTodo = {
          id: uuidv4(),
          text: this.text,
          isDone: false,
        };

        this.$emit("add-todo-event", newTodo);
        this.text = "";
      }
    },
  },
};
</script>
