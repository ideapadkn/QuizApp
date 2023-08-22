<script setup>
  import { defineProps } from 'vue'
  import { useRouter } from 'vue-router';

  const router = useRouter()
  const {quiz} = defineProps(['quiz'])

  const navigateToQuiz = () => {
    router.push(`/quiz/${quiz.id}`)
  }
</script>

<template>
  <div 
    @click="navigateToQuiz"
    class="card w-80 overflow-hidden rounded mb-9 mr-5 cursor-pointer hover:scale-105 transition-all"
  >
    <img 
      :src="quiz.img" 
      alt="math"
      class="w-full m-0 h-[200px]"
    >
    <div class="card-text p-2">
      <h2 class="font-bold">{{ quiz.name }}</h2>
      <p>{{ quiz.questions.length }} questions</p>
    </div>  
  </div>
</template>