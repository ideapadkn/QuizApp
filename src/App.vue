<script setup>
  import q from './data/quizes.json'
  import {ref, watch} from 'vue'

  const quizes = ref(q)
  const search = ref('')

  watch(search, () => {
    quizes.value = q.filter(quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
  })
</script>

<template>
  <div class="container mx-auto">
    <header class="header mb-2.5 mt-2.5 flex items-center">
      <h1 class="text-4xl inline-block font-bold mr-7">Quizes</h1>
      <input 
        v-model.trim="search"
        type="text"
        placeholder="Search..."
        class="border-2 inline-block border-none focus:outline-none rounded-md bg-slate-200 p-1"
      >
    </header>
    <div class="options-container flex flex-wrap mt-10">
      <div 
        v-for="quiz in quizes"
        :key="quiz.id"
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
    </div>
  </div>
</template>

<style>
.container {
  max-width: 1100px;
  margin: 0 auto;
  padding: 0 15px;
}
/* CARD */
.card {
  box-shadow: 1px 1px 10px rgba(1, 1, 1, 0.1);
}
</style>
