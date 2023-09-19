<script setup>
import { ref, reactive } from "vue"
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
    if (opt == true) { // Går ej in i loopen om opt.isCorrect?
      score.value++
    } else if (opt == false) { }
    console.log("score: ", score.value)
  } else { // om currQ > questions.Length
    if (opt == true) {
      score.value++
    } else if (opt == false) { }
    console.log("end of the quiz, total score: ", score.value) // TODO: showScore(true) och visa "div score-section"
  }
}
</script>

<template>
  <header></header>
  <main>
    <!-- <div class="score-section">You scored {{ score }} out of {{ questions.length }} </div> -->
    <div class="question-section">
      <div class="question-count">
        Question {{ currentQuestion + 1 }} / {{ questions.length }}
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
  </main>
</template>

<style scoped></style>
