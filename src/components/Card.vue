<script setup>
  import { defineProps } from 'vue'

  const {quiz} = defineProps(['quiz'])
</script>

<template>
  <div 
    class="card w-80 overflow-hidden rounded mb-9 mr-5 cursor-pointer"
  >
    <img 
      :src="quiz.img" 
      alt="math"
      class="w-full m-0"
    >
    <div class="card-text p-2">
      <h2 class="font-bold">{{ quiz.name }}</h2>
      <p>{{ quiz.questions.length }} questions</p>
    </div>
  </div>
</template>