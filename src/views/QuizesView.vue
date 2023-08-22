<script setup>
  import q from '../data/quizes.json'
  import {ref, watch} from 'vue'
  import Card from '../components/Card.vue'

  const quizes = ref(q)
  const search = ref('')

  watch(search, () => {
    quizes.value = q.filter(quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
  })
  
</script>

<template>
  <div>
    <header class="header mb-2.5 mt-2.5 flex items-center">
      <h1 class="text-4xl inline-block font-bold mr-7">Quizes</h1>
      <input
        v-model.trim="search"
        type="text"
        placeholder="Search..."
        class="inline-block border-none focus:outline-none rounded-md bg-slate-200 py-1 px-2"
      >
    </header>
    <div class="options-container flex flex-wrap mt-10">
      <Card 
        v-for="quiz in quizes"
        :key="quiz.id"
        :quiz="quiz"
      />
      <!-- <div 
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
      </div> -->
    </div>
  </div>
</template>

<style>
/* CARD */
.card {
  box-shadow: 1px 1px 10px rgba(1, 1, 1, 0.1);
}
</style>
