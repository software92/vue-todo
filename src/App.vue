<script setup lang="ts">
import { onMounted, ref } from "vue";
import TodoInput from "./components/TodoInput.vue";
import TodoListItem from "./components/TodoListItem.vue";

export interface Todo {
  title: string;
  done: boolean;
}

const STORAGE_KEY = "vue_3_ts_key";

const storage = {
  save(value: Todo[]) {
    const parsed = JSON.stringify(value);
    localStorage.setItem(STORAGE_KEY, parsed);
  },
  fetch(): Todo[] {
    const todoItems = localStorage.getItem(STORAGE_KEY) || "[]";
    const result = JSON.parse(todoItems);
    return result;
  },
};
const todoText = ref<string>("");
const todoItems = ref<Todo[]>([]);

const updateTodoText = (value: string) => {
  todoText.value = value;
};
const addTodoItem = () => {
  const value = todoText.value;
  if (value === "") return;
  const todo: Todo = {
    title: value,
    done: false,
  };
  todoItems.value.push(todo);
  storage.save(todoItems.value);
  initTodos();
};
const initTodos = () => {
  todoText.value = "";
};

const fetchTodos = () => {
  // axios.get('todos'), order
  //fetch return data를 Todo로 지정해서, a,b의 타입을 자동 추론(이 때 타입 정의 안해도됨)
  todoItems.value = storage.fetch().sort((a, b) => {
    if (a.title < b.title) {
      return -1;
    }
    if (a.title > b.title) {
      return 1;
    }
    return 0;
  });
};
const deleteTodoInTodos = (index: number) => {
  console.log("delete", index);
  // const deleteIdx = todoItems.value.findIndex((item: string) => item === value);
  todoItems.value.splice(index, 1);
  storage.save(todoItems.value);
};

const toggleTodoDoneState = (todo: Todo, index: number) => {
  // todoItems.value[index].done = !todoItems.value[index].done;
  console.log("todddo", todo);
  todoItems.value.splice(index, 1, {
    ...todo,
    done: !todo.done,
  });
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
      @toggle="toggleTodoDoneState"
    ></TodoListItem>
  </ul>
</template>

<style scoped></style>
