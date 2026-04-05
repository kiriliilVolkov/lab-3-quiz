<script setup lang="ts">
import { computed, ref } from 'vue'
import AnwersComponent from './components/AnwersComponent.vue'
import NavigationComponent from './components/NavigationComponent.vue'
import NextComponent from './components/NextComponent.vue'
import QuestionComponent from './components/QuestionComponent.vue'
import data from './data/data.json'
import ResultComponent from './components/ResultComponent.vue'

const current = ref(1)
const questions = data.questions
const currentQuestion = computed(() => questions[current.value - 1])
const choice = ref<number>()
const total = ref(0)

const choiceHandler = (value: number) => {
  choice.value = value
  if (currentQuestion.value?.correct === value + 1) {
    total.value += 1
  }
}
</script>

<template>
  <div>
    <img src="../src/assets/fl1.png" class="decor-left" />
    <img src="../src/assets/fl2.png" class="decor-right" />

    <div class="mainframe">
      <NavigationComponent :total="data.questions.length" :current="current" />
      <div class="questionButton">
        <div class="question">
          <QuestionComponent v-if="currentQuestion" :text="currentQuestion.text" />
        </div>
        <NextComponent v-if="choice !== undefined" @next="((choice = undefined), (current += 1))" />
      </div>
      <AnwersComponent
        v-if="currentQuestion"
        :answers="currentQuestion.answers"
        :disabled="choice !== undefined"
        :selected="choice"
        :correct="currentQuestion.correct - 1"
        @choice="choiceHandler"
      />
      <ResultComponent v-if="!currentQuestion" :total="total" />
    </div>
  </div>
</template>

<style scored>
.mainframe {
  height: 813px;
  width: 1095px;
  background-image: linear-gradient(#003dce, #15aaff, #14a4fc, #003dce);
  border-radius: 51px;
  box-shadow: 9px 9px 0 0 #0060d9;
  padding: 73px;
  position: relative;
  z-index: 10;
}

.questionButton {
  display: flex;
}

.question {
  align-items: center;
  display: flex;
  transform: translate(25%, 0);
}

.decor-left {
  left: 0;
  transform: translate(-58%, 143%);

  top: 50%;
  z-index: 1;
  pointer-events: none;
}
.decor-right {
  right: 0;
  transform: translate(95%, 92%);

  top: 50%;
  z-index: 1;
  pointer-events: none;
}
</style>
