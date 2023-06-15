<script setup lang="ts">
import { ref } from "vue";
import TodoInput from "./components/TodoInput.vue";

const todoText = ref("");
const updateTodos = (value: string) => {
  todoText.value = value;
};
const addTodo = () => {
  const value = todoText.value;
  if (value === "") return;
  localStorage.setItem(value, value);
  initTodos();
};
const initTodos = () => {
  todoText.value = "";
};
</script>

<template>
  <form @submit="addTodo">
    <h1>Vue Todo with TS</h1>
    <TodoInput :value="todoText" @input="updateTodos" />

    <button>add</button>
  </form>
</template>

<style scoped></style>
