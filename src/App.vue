<!-- snippet: vbase-3-ts -->
<template>
  <div>
    <h1>Vue Todo with TS</h1>
  </div>
  <TodoInput :item="todoText" />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TodoInput from "./components/TodoInput.vue";

export default defineComponent({
  components: { TodoInput },
  data() {
    return {
      todoText: "",
    };
  },
  // setup() {
  //   return {};
  // },
});
</script>

<style scoped></style>
