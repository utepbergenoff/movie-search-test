<template>
  <div class="movie-card">
    <div class="poster-wrapper">
      <img :src="movie.Poster !== 'N/A' ? movie.Poster : placeholder" alt="Poster" class="poster" />
    </div>
    <div class="movie-info">
      <div><b>Name:</b> {{ movie.Title }}</div>
      <div><b>Year:</b> {{ movie.Year }}</div>
      <div><b>imdbID:</b> {{ movie.imdbID }}</div>
      <div><b>Type:</b> {{ movie.Type }}</div>
    </div>
  </div>
</template>

<script setup>
const placeholder = 'https://via.placeholder.com/150x200?text=No+Image'
defineProps(['movie'])
</script>

<style scoped>
.movie-card {
  border: 1px solid #b3c6ff;
  border-radius: 12px;
  padding: 24px 16px 16px 16px;
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 340px;
  background: #fff;
  transition: box-shadow 0.2s;
}
.movie-card:hover {
  box-shadow: 0 4px 24px 0 #e3e8f7;
}
.poster-wrapper {
  width: 150px;
  height: 200px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 18px;
  background: #f5f7fa;
  border-radius: 8px;
  overflow: hidden;
}
.poster {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.movie-info {
  font-size: 1rem;
  text-align: left;
  width: 100%;
  margin-top: 8px;
}
.movie-info > div {
  margin-bottom: 4px;
}
</style> 