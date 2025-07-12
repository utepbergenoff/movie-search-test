<template>
  <div class="search-info">
    You searched for: <b>{{ query }}</b>
    <span class="results-badge">{{ total }} results</span>
  </div>
</template>

<script setup>
defineProps(['query', 'total'])
</script>

<style scoped>
.search-info {
  font-size: 1.15rem;
  margin-bottom: 32px;
  display: flex;
  align-items: center;
  gap: 16px;
}
.results-badge {
  background: #3d5afe;
  color: #fff;
  border-radius: 6px;
  padding: 4px 12px;
  font-size: 0.95rem;
  margin-left: 8px;
}
</style> 