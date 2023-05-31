<script setup>
import { ref } from 'vue'


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
];

const currentQuestion = ref(0)
const showScore = ref(false)
const score = ref(0)

const handleAnswerButtonClick = () => {
  alert('du klickade opt1' + 'du har ' + score.value + 'poäng')

  const nextQuestion = currentQuestion + 1
}
</script>

<template>
  <header>DM-quiz</header>
  <main>
    <div class="score-section">du har {{ score }} poäng av {{ questions.length }} poäng</div>
    <div class="question-section">
      <div class="question-count">fråga {{ currentQuestion +1 }} av {{ questions.length }}</div>
      <div class="question-text">{{ questions[0].questionText }}</div>
    </div>
    <div class="answer-section"> 
      <button v-for="opt in questions[0].answerOptions">{{ opt.answerText }}</button>
    </div>
  </main>
</template>

<style scoped></style>
