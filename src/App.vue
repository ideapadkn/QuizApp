<script setup>
import { RouterView } from 'vue-router'
</script>

<template>
  <div class="container mx-auto">
    <RouterView />
  </div>
</template>

<style>
.container {
  max-width: 1100px;
  margin: 0 auto;
  padding: 0 15px;
}
</style>