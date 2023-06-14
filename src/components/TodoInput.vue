<template>
  <div>
    <label for="todo-input"></label>
    <input id="todo-input" type="text" :value="item" />
    <button @click="addTodo" type="button">add</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: ["item"],
  methods: {
    addTodo() {
      console.log("add");
    },
  },
  // setup() {
  //   console.log("setup");
  //   return {};
  // },
  // mounted() {
  //   addTodo(){
  //     console.log('add')
  //   }
  // }
});
</script>

<style scoped></style>
