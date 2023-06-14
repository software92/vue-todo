<template>
  <div>
    <h1>Vue Todo with TS</h1>
    <TodoInput :item="todoText" @input="updateTodoText"></TodoInput>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TodoInput from "./components/TodoInput.vue";

export default defineComponent({
  components: { TodoInput },
  setup() {
    return {
      todoText: "",
    };
  },
  methods: {
    updateTodoText(value: any) {
      this.todoText = value;
    },
  },
});
</script>

<style scoped></style>
