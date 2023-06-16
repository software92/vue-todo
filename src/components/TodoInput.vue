<script setup lang="ts">
interface Props {
  value: string;
}

defineProps<Props>();
const emit = defineEmits(["input", "add"]);
const changeValue = (event: Event) => {
  // unsafe
  const eventTarget = event.target as HTMLInputElement;

  // console.log(event);
  // if (!event.target) return;

  emit("input", eventTarget.value);
  // event.target!.value: non-null assertion type
  // emit("input", event.target!.value);
};

const addTodo = () => {
  emit("add");
};
</script>

<template>
  <h2>자식 컴포넌트입니다!</h2>
  <input :value="value" @input="changeValue" />
  <button @click="addTodo">add</button>
  <!-- <input  -->
</template>
