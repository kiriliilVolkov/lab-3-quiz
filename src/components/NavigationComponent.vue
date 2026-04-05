<template>
  <div class="nav">
    <div
      v-for="item in total"
      :key="item"
      class="nav-item"
      :class="item <= current ? 'active' : ''"
    ></div>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  total: number
  current: number
}>()
</script>

<style scoped>
.nav {
  display: flex;
  gap: 2px;
  padding-top: 40px;
}

.nav-item {
  flex: 1 1 100%;
  height: 6px;
  background-color: gray;
  width: 134;
  height: 6;
  top: 178px;
  left: 490px;
  opacity: 1;
  border-top-left-radius: 10px;
  border-bottom-left-radius: 10px;
}

.active {
  background-color: #6bff2f;
}
</style>
