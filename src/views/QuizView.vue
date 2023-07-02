<script setup>
  import Question from '../components/Question.vue'
  import QuizHeader from '../components/QuizHeader.vue'
  import { useRoute } from 'vue-router'
  import { ref, watch } from 'vue';
  import quizes from '../data/quizes.json'

  const route = useRoute()

  const quizId = parseInt(route.params.id)

  const quiz = quizes.find(q => q.id === quizId)

  const currentQuestionsIndex = ref(0)

  const questionsStatus = ref(`${currentQuestionsIndex.value}/${quiz.questions.length}`)

  watch(() => currentQuestionsIndex.value, () => {
    questionsStatus.value = `${currentQuestionsIndex.value}/${quiz.questions.length}`
  })
</script>

<template>
  <div>
    <QuizHeader 
      :questionsStatus="questionsStatus"
    />
    <div>
      <Question 
        :questions="quiz.questions[currentQuestionsIndex]"
      />
    </div>
    <button @click="currentQuestionsIndex++">
      Next Question
    </button>
  </div>
</template>