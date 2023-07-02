<script setup>
  import { defineProps } from 'vue';
  import { RouterLink } from 'vue-router';

  const {
    quizQuestionLength, 
    numberOfCorrectAnswers
  } = defineProps([
    'quizQuestionLength', 
    'numberOfCorrectAnswers'
  ])
</script>

<template>
  <div class="results text-center py-16">
    <p class="text-2xl">Your Results ...</p>
    <h1 class="text-8xl mb-5">
      {{ numberOfCorrectAnswers }} / {{ quizQuestionLength }}
    </h1>
    <RouterLink to="/">Go Back</RouterLink>
  </div>
</template>