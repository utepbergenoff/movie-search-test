<template>
  <div class="movie-grid">
    <MovieCard v-for="movie in movies.slice(0, 8)" :key="movie.imdbID" :movie="movie" />
  </div>
</template>

<script setup>
import MovieCard from './MovieCard.vue'
defineProps(['movies'])
</script>

<style scoped>
.movie-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(2, 1fr);
  gap: 40px 32px;
  margin-bottom: 40px;
}
</style> 