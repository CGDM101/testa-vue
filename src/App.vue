<script setup>
import { ref, reactive } from 'vue'
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

const handleAnswerButtonClick = (opt) => {
  if(currentQuestion.value < questions.length) {
    currentQuestion.value++
    if(opt.isCorrect == true) { // går inte in i denna loop
      score.value++
      console.log(score.value)
      console.log(currentQuestion.value)  
    }
    alert('du klickade' + opt + 'du har ' + score.value + 'poäng') // TODO: Opt blir "true"/"false"
  } else {
    alert('You reached the end of the quiz') // TODO: Visa sista vy i stället f alert: showScore(true)  
    console.log(score.value)
    console.log(currentQuestion.value)
  }
}
</script>

// div score-section ska bara synas om showScore(true)
<template>
  <header>Camillas quiz</header>
  <main>
    <div class="score-section">du har {{ score }} poäng av {{ questions.length }} poäng</div>
    <div class="question-section">
      <div class="question-count">fråga {{ currentQuestion +1 }} av {{ questions.length }}</div>
      <div class="question-text">{{ questions[currentQuestion].questionText }}</div>
    </div>
    <div class="answer-section"> 
      <button @click="handleAnswerButtonClick(opt.isCorrect)" v-for="opt in questions[currentQuestion].answerOptions" >{{ opt.answerText }}</button>
    </div>
  </main>
</template>

<style scoped></style>
