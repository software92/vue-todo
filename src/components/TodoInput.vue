<template>
  <div>
    <label for="todo-input">오늘 할 일: </label>
    <input id="todo-input" type="text" :value="item" @input="handleInput" />
    <button type="button">추가</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: ["item"],
  methods: {
    handleInput(event: any) {
      console.log("event", event.target.value);
      this.$emit("input", event.target.value);
    },
  },
  // setup() {
  //   return {};
  // },
});
</script>

<style scoped></style>
