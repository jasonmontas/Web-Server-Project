<script setup lang="ts">
import { RouterView } from 'vue-router'
import NavBar from './components/NavBar.vue'
</script>

<template>
  <header>
    <NavBar />
  </header>

  <div class="container body-container">
    <RouterView />
  </div>
</template>

<style scoped>
body {
  background-color: aliceblue;
}

.body-container {
  background-color: white;
  height: 100vh;
  padding: 1rem;
}
</style>
