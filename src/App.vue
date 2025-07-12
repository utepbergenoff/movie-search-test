<script setup>
import { ref, computed, watch } from 'vue'
import Header from './components/Header.vue'
import SearchInfo from './components/SearchInfo.vue'
import MovieGrid from './components/MovieGrid.vue'
import Pagination from './components/Pagination.vue'

const query = ref('Batman')
const page = ref(1)
const movies = ref([])
const totalResults = ref(0)

const totalPages = computed(() => Math.ceil(totalResults.value / 10))

async function fetchMovies() {
  const res = await fetch(`https://www.omdbapi.com/?apikey=8523cbb8&s=${encodeURIComponent(query.value)}&page=${page.value}`)
  const data = await res.json()
  movies.value = data.Search || []
  totalResults.value = parseInt(data.totalResults) || 0
}

function onSearch(newQuery) {
  query.value = newQuery
  page.value = 1
}

function onPageChange(newPage) {
  page.value = newPage
}

watch([query, page], fetchMovies, { immediate: true })
</script>

<template>
  <div class="app-container">
    <Header @search="onSearch" />
    <SearchInfo :query="query" :total="totalResults" />
    <MovieGrid :movies="movies" />
    <Pagination :current="page" :total="totalPages" @change="onPageChange" />
  </div>
</template>

<style scoped>
.app-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 32px 16px;
  font-family: 'Inter', Arial, sans-serif;
  background: #fff;
  min-height: 100vh;
  box-sizing: border-box;
  color: #111;
}
</style>

<style>
body {
  background: #fff !important;
  color: #111 !important;
}
</style>
