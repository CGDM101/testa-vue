<script setup>
import { ref } from "vue"
const questions = [
  {
    questionText: "What is the capital of France?",
    answerOptions: [
      { answerText: "New York", isCorrect: false },
      { answerText: "London", isCorrect: false },
      { answerText: "Paris", isCorrect: true },
      { answerText: "Dublin", isCorrect: false },
    ],
  },
  {
    questionText: "Who is CEO of Tesla?",
    answerOptions: [
      { answerText: "Jeff Bezos", isCorrect: false },
      { answerText: "Elon Musk", isCorrect: true },
      { answerText: "Bill Gates", isCorrect: false },
      { answerText: "Tony Stark", isCorrect: false },
    ],
  },
  {
    questionText: "The iPhone was created by which company?",
    answerOptions: [
      { answerText: "Apple", isCorrect: true },
      { answerText: "Intel", isCorrect: false },
      { answerText: "Amazon", isCorrect: false },
      { answerText: "Microsoft", isCorrect: false },
    ],
  },
  {
    questionText: "How many Harry Potter books are there?",
    answerOptions: [
      { answerText: "1", isCorrect: false },
      { answerText: "4", isCorrect: false },
      { answerText: "6", isCorrect: false },
      { answerText: "7", isCorrect: true },
    ],
  },
]

const currentQuestion = ref(0)
const showScore = ref(false)
const score = ref(0)

const handleAnswerButtonClick = (opt) => {
  if (currentQuestion.value < questions.length - 1) {
    currentQuestion.value++
    if (opt == true) {
      score.value++
    } else if (opt == false) { }
  } else {
    if (opt == true) {
      score.value++
    } else if (opt == false) { }
    showScore.value = ref(true)
  }
}
</script>

<template>
  <header></header>
  <main class="app">
    <div v-if="showScore" class="score-section">You scored {{ score }} out of {{ questions.length }} </div>
    <div class="app" v-else>
      <div class="question-section">
        <div class="question-count"><span>Question {{ currentQuestion + 1 }}</span>
          / {{ questions.length }}
        </div>
        <div class="question-text">
          {{ questions[currentQuestion].questionText }}
        </div>
      </div>
      <div class="answer-section">
        <button @click="handleAnswerButtonClick(opt.isCorrect)" v-for="opt in questions[currentQuestion].answerOptions">
          {{ opt.answerText }}
        </button>
      </div>
    </div>
  </main>
</template>

<style scoped></style>
