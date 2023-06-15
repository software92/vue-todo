<script setup lang="ts">
interface Props {
  value: string;
}

defineProps<Props>();
const emit = defineEmits(["input"]);
const changeValue = (event: InputEvent) => {
  // unsafe
  const eventTarget = event.target as HTMLInputElement;

  // console.log(event);
  // if (!event.target) return;

  emit("input", eventTarget.value);
  // event.target!.value: non-null assertion type
  // emit("input", event.target!.value);
};
</script>

<template>
  <h2>자식 컴포넌트입니다!</h2>
  <input :value="value" @input="changeValue" />
  <!-- <input  -->
</template>
