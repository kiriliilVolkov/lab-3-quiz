<template>
  <div class="wrapper">
    <div class="card">
      <!-- прогресс -->
      <div class="progress">
        <div class="bar"></div>
      </div>

      <!-- текст -->
      <div class="text">
        <h3>Название путешествия.</h3>
        <p>
          Судя по мультфильму, Бременские музыканты могли ездить только на одном виде транспорта.
          Каком?
        </p>
      </div>

      <!-- ответы -->
      <div class="answers">
        <div
          v-for="(item, i) in answers"
          :key="i"
          class="answer"
          :class="getClass(i)"
          @click="select(i)"
        >
          <img :src="item.img" />
        </div>
      </div>

      <!-- кнопка -->
      <div v-if="answered" class="next">▶</div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const answers = ref([
  { img: '/img/1.png', correct: false },
  { img: '/img/2.png', correct: true },
  { img: '/img/3.png', correct: false },
  { img: '/img/4.png', correct: false },
])

const selected = ref(null)
const answered = ref(false)

const select = (i) => {
  if (answered.value) return
  selected.value = i
  answered.value = true
}

const getClass = (i) => {
  if (!answered.value) return ''
  if (answers.value[i].correct) return 'correct'
  if (selected.value === i) return 'wrong'
  return ''
}
</script>

<style scoped>
.wrapper {
  height: 100vh;
  background: #2c0c59;
  display: flex;
  justify-content: center;
  align-items: center;
}

.card {
  width: 600px;
  padding: 30px;
  border-radius: 20px;
  background: linear-gradient(135deg, #5aa9ff, #3a6edc);
  position: relative;
}

.progress {
  height: 6px;
  background: rgba(255, 255, 255, 0.2);
  border-radius: 10px;
  margin-bottom: 20px;
}

.bar {
  width: 30%;
  height: 100%;
  background: #9cff00;
  border-radius: 10px;
}

.text {
  text-align: center;
  color: white;
}

.answers {
  display: flex;
  gap: 15px;
  margin-top: 20px;
}

.answer {
  width: 100px;
  height: 100px;
  border-radius: 12px;
  overflow: hidden;
  border: 3px solid transparent;
  cursor: pointer;
}

.answer img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.correct {
  border-color: #00ff88;
}

.wrong {
  border-color: red;
}

.next {
  position: absolute;
  right: 20px;
  top: 50%;
  transform: translateY(-50%);
  background: #9cff00;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
