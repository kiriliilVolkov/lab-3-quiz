<template>
  <button class="but" :class="stateClass" @click="emit('click')" :disabled="disabled">
    <img :src="answer" />
  </button>
</template>

<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps<{
  answer: string
  disabled: boolean
  selected?: number
  correct: number
  index: number
}>()

const emit = defineEmits<{
  click: []
}>()

const stateClass = computed(() => {
  if (props.selected === undefined) return ''

  if (props.index === props.correct) return 'correct'
  if (props.index === props.selected) return 'wrong'

  return ''
})
</script>

<style scoped>
.but {
  width: 200px;
  height: 250px;
  border-radius: 20px;
  margin: 0 20px 50px 20px;
}

.correct {
  border: 8px solid #00ff88;
  background-color: #00ff88;
  box-shadow: 15px 15px 0 0 #00ff88;
}

.wrong {
  border: 8px solid #ff3b3b;
  background-color: #ff3b3b;
  box-shadow: 15px 15px 0 0 #ff3b3b;
}

img {
  height: 250px;
  width: 200px;
  border-radius: 20px;
  object-fit: cover;
  pointer-events: none;
  transform: translate(-6px, -2px);
}
</style>
