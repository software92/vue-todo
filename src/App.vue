<!-- snippet: vbase-3-ts -->
<template>
  <div>
    <h1>Vue Todo with TS</h1>
  </div>
  <TodoInput />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TodoInput from "./components/TodoInput.vue";

export default defineComponent({
  setup() {
    return {};
  },
  components: { TodoInput },
});
</script>

<style scoped></style>
