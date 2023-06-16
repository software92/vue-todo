<script lang="ts" setup>
const props = defineProps({ todo: { type: String }, index: { type: Number } });
const emit = defineEmits(["delete"]);
// import { defineComponent } from "vue";

// export default defineComponent({
//   setup() {
//     return {};
//   },
// });

const deleteTodo = () => {
  emit("delete", props.index);
};
</script>

<template>
  <li>
    <span>{{ todo }}</span>
    <button @click="deleteTodo">삭제</button>
    <!-- <p>아이템 x</p> -->
    <!-- <slot>{{ todo }}</slot> -->
  </li>
</template>

<style scoped></style>
