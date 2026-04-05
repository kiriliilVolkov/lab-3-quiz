<template>
  <button class="butNext" @click="emit('next')">
    <img src="../assets\but.svg" alt="NEXT" />
  </button>
</template>

<script setup lang="ts">
const emit = defineEmits<{
  next: []
}>()
</script>

<style scoped>
.butNext {
  height: 50px;
  width: 50px;
  cursor: pointer;
  background-color: transparent;
  border: 0;
  margin: auto;
  transform: translate(-50%, -50%);
}
</style>
