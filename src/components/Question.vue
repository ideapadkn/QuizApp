<script setup>
  import { defineProps, defineEmits } from 'vue'

  const { questions } = defineProps(['questions'])

  const emit = defineEmits(['selectOption'])

  const emitSelectedOption = (isCorrect) => {
    emit('selectOption', isCorrect)
  }
</script>

<template>
  <div class="question-container mt-5">
    <h1 class="question text-5xl mb-5">
      {{ questions.text }}
    </h1>
  </div>
  <div class="options-container">
    <div  
      v-for="option in questions.options"
      :key="option.id"
      class="option flex mb-5 cursor-pointer"
      @click="emitSelectedOption(option.isCorrect)"
    >
      <p class="option-label bg-indigo-200 w-14 h-14 text-3xl flex items-center justify-center">
        {{ option.label }}
      </p>
      <div class="option-value bg-indigo-50 w-full text-3xl pt-2 px-5">
        <p>
          {{ option.text }}
        </p>
      </div>
    </div>
  </div>
</template>