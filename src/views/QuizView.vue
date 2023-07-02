<script setup>
  import Question from '../components/Question.vue'
  import QuizHeader from '../components/QuizHeader.vue'
  import Result from '../components/Result.vue'
  import { useRoute } from 'vue-router'
  import { ref, computed } from 'vue';
  import quizes from '../data/quizes.json'

  const route = useRoute()

  const quizId = parseInt(route.params.id)

  const quiz = quizes.find(q => q.id === quizId)

  const currentQuestionsIndex = ref(0)

  const numberOfCorrectAnswers = ref(0)

  const showResults = ref(false)

  // const questionsStatus = ref(`${currentQuestionsIndex.value}/${quiz.questions.length}`)

  // watch(() => currentQuestionsIndex.value, () => {
  //   questionsStatus.value = `${currentQuestionsIndex.value}/${quiz.questions.length}`
  // })

  const questionsStatus = computed(() => {
    return `${currentQuestionsIndex.value}/${quiz.questions.length}`
  })
  const barPercentage = computed(() => {
    return `${currentQuestionsIndex.value/quiz.questions.length * 100}%`
  })

  const onOptionSelected = (isCorrect) => {
    if(isCorrect) {
      numberOfCorrectAnswers.value++
    }

    if(quiz.questions.length - 1 === currentQuestionsIndex.value) {
      showResults.value = true
    }

    currentQuestionsIndex.value++
  }
</script>

<template>
  <div>
    <QuizHeader 
      :questionsStatus="questionsStatus"
      :barPercentage="barPercentage"
    />
    <div>
      <Question 
        v-if="!showResults"
        :questions="quiz.questions[currentQuestionsIndex]"
        @selectOption="onOptionSelected"
      />
      <Result 
        v-else 
        :quizQuestionLength="quiz.questions.length"
        :numberOfCorrectAnswers="numberOfCorrectAnswers"
      />
    </div>
  </div>
</template>