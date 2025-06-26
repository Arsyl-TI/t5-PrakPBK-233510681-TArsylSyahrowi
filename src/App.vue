<template>
  <div class="app">
    <Navbar />
    <main class="content">
      <router-view />
    </main>
  </div>
</template>

<script setup>
import Navbar from './components/Navbar.vue'
</script>

<style scoped>
.app {
  font-family: Arial, sans-serif;
}

.content {
  padding: 20px;
  max-width: 700px;
  margin: auto;
}

.main-content {
  margin-left: 250px; /* Same as navbar width */
  padding: 20px;
}

@media (max-width: 768px) {
  .main-content {
    margin-left: 70px; /* Same as collapsed navbar width */
  }
}
</style>
