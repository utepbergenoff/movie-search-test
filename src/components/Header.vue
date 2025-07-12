<template>
  <header class="header">
    <div class="logo">
      <span class="logo-icon blue">🎬</span>
      <span class="logo-text">MOOZ</span>
    </div>
    <div class="search-container">
      <input
        v-model="search"
        @keyup.enter="emitSearch"
        type="text"
        placeholder="Search..."
        class="search-input"
      />
      <button class="search-btn" @click="emitSearch">
        <span class="blue">🔍</span>
      </button>
    </div>
    <div class="user">
      <span class="user-icon blue">👤</span>
      <span>Profile name</span>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue'
const emit = defineEmits(['search'])
const search = ref('Batman')
function emitSearch() {
  emit('search', search.value)
}
</script>

<style scoped>
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 24px 0 32px 0;
}
.logo {
  display: flex;
  align-items: center;
  font-size: 1.5rem;
  font-weight: bold;
}
.logo-icon {
  font-size: 2rem;
  margin-right: 8px;
}
.search-container {
  display: flex;
  align-items: center;
  flex: 1;
  max-width: 400px;
  margin: 0 32px;
}
.search-input {
  width: 100%;
  padding: 8px 12px;
  border: 1px solid #e0e0e0;
  border-radius: 6px 0 0 6px;
  outline: none;
  font-size: 1rem;
}
.search-btn {
  padding: 8px 16px;
  border: 1px solid #e0e0e0;
  border-left: none;
  background: #f5f7fa;
  border-radius: 0 6px 6px 0;
  cursor: pointer;
  font-size: 1rem;
}
.user {
  display: flex;
  align-items: center;
  font-size: 1rem;
  color: #222;
}
.user-icon {
  font-size: 1.3rem;
  margin-right: 6px;
}
.blue {
  color: #3d5afe;
}
</style> 