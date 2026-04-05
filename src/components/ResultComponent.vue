<template>
  <div>
    <p>результат: {{ result.text }}</p>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue'
import data from '../data/data.json'
const props = defineProps<{
  total: number
}>()
const result = computed(() =>
  data.result.reduce((prev, current) => (prev.count <= props.total ? current : prev)),
)
</script>

<style scoped>
p {
  font-family: PT Sans Caption;
  font-weight: 700;
  font-size: 22px;
  line-height: 40px;
  letter-spacing: 0%;
  text-align: center;
}
</style>
