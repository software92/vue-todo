<script setup lang="ts">
import { onMounted, ref } from "vue";
import TodoInput from "./components/TodoInput.vue";
import TodoListItem from "./components/TodoListItem.vue";

const STORAGE_KEY = "vue_3_ts_key";

const storage = {
  save(value: any[]) {
    const parsed = JSON.stringify(value);
    localStorage.setItem(STORAGE_KEY, parsed);
  },
  fetch() {
    const todoItems = localStorage.getItem(STORAGE_KEY) || "[]";
    const result = JSON.parse(todoItems);
    return result;
  },
};
const todoText = ref("");
const todoItems: any = ref([]);

const updateTodoText = (value: string) => {
  todoText.value = value;
};
const addTodoItem = () => {
  const value = todoText.value;
  if (value === "") return;
  todoItems.value.push(value);
  storage.save(todoItems.value);
  initTodos();
};
const initTodos = () => {
  todoText.value = "";
};

const fetchTodos = () => {
  todoItems.value = storage.fetch();
};
const deleteTodoInTodos = (index: number) => {
  console.log("delete", index);
  // const deleteIdx = todoItems.value.findIndex((item: string) => item === value);
  todoItems.value.splice(index, 1);
  storage.save(todoItems.value);
};

// lifecycle
onMounted(() => {
  fetchTodos();
});
</script>

<template>
  <h1>Vue Todo with TS</h1>
  <TodoInput :value="todoText" @input="updateTodoText" @add="addTodoItem" />
  <ul>
    <TodoListItem
      v-for="(todo, i) in todoItems"
      :key="i"
      :todo="todo"
      :index="i"
      @delete="deleteTodoInTodos"
    ></TodoListItem>
  </ul>
</template>

<style scoped></style>
