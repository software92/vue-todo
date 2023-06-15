<script setup lang="ts">
defineProps<{ value: string }>();
const emit = defineEmits(["input"]);
const changeValue = (e: any) => {
  // console.log("input", e.target.value);
  emit("input", e.target.value);
};
</script>

<template>
  <h2>자식 컴포넌트입니다!</h2>
  <input :value="value" @input="changeValue" />
  <!-- <input  -->
</template>
