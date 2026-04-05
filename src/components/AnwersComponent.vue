<template>
  <div class="answers">
    <AnswerComponent
      v-for="(answer, index) in answers"
      :key="index"
      :answer="answer"
      :disabled="disabled"
      :selected="selected"
      :correct="correct"
      :index="index"
      @click="emit('choice', index)"
    />
  </div>
</template>

<script setup lang="ts">
import AnswerComponent from './AnswerComponent.vue'
defineProps<{
  answers: string[]
  disabled: boolean
  selected?: number
  correct: number
}>()
const emit = defineEmits<{
  choice: [value: number]
}>()
</script>

<style scored>
.answers {
  display: flex;
  justify-content: space-between;
}
</style>
