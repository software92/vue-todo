<script lang="ts" setup>
import { Todo } from "@/App.vue";
import { computed } from "@vue/reactivity";
import { PropType } from "vue";

const props = defineProps({
  todo: { type: Object as PropType<Todo> },
  index: { type: Number },
});

const emit = defineEmits(["delete", "toggle"]);

const deleteTodo = () => {
  emit("delete", props.index);
};
const toggleTodo = () => {
  emit("toggle", props.todo, props.index);
};
const isCompletedClass = computed((): string | null =>
  props.todo?.done ? "complete" : null
);
</script>

<template>
  <li>
    <span class="todo" :class="isCompletedClass" @click="toggleTodo">{{
      todo?.title
    }}</span>
    <button @click="deleteTodo">삭제</button>
  </li>
</template>

<style scoped>
.todo {
  cursor: pointer;
}
.complete {
  text-decoration: line-through;
}
</style>
