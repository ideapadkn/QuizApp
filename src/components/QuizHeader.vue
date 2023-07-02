<script setup>
  import { defineProps } from 'vue';

  const { 
    questionsStatus, 
    barPercentage 
  } = defineProps([
    'questionsStatus', 
    'barPercentage'
  ])
</script>

<template>
  <header class="mt-5">
    <h4 class="text-3xl  mb-5">Questions {{ questionsStatus }}</h4>
    <div class="bar w-80 h-12 border-2 border-b-indigo-100 ">
      <div 
        class="complition h-full w-0 bg-indigo-100"
        :style="{width: barPercentage}"
      >
      </div>
    </div>
  </header>
</template>