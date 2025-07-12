<template>
  <div class="pagination">
    <button :disabled="current === 1" @click="change(current - 1)">&lt;</button>
    <template v-for="n in pages" :key="n + '-page'">
      <span v-if="n === '...'" class="dots">...</span>
      <button
        v-else
        :class="{ active: n === current }"
        @click="change(n)"
      >{{ n }}</button>
    </template>
    <button :disabled="current === total" @click="change(current + 1)">&gt;</button>
  </div>
</template>

<script setup>
import { computed } from 'vue'
const props = defineProps(['current', 'total'])
const emit = defineEmits(['change'])

const pages = computed(() => {
  const arr = []
  if (props.total <= 7) {
    for (let i = 1; i <= props.total; i++) arr.push(i)
  } else {
    arr.push(1)
    if (props.current > 4) arr.push('...')
    for (let i = Math.max(2, props.current - 1); i <= Math.min(props.total - 1, props.current + 1); i++) {
      if (i > 1 && i < props.total) arr.push(i)
    }
    if (props.current < props.total - 3) arr.push('...')
    arr.push(props.total)
  }
  return arr
})

function change(n) {
  if (typeof n === 'number' && n !== props.current && n >= 1 && n <= props.total) emit('change', n)
}
</script>

<style scoped>
.pagination {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 4px;
  margin-bottom: 32px;
}
.pagination button {
  background: #fff;
  border: 1px solid #e0e0e0;
  border-radius: 4px;
  padding: 6px 12px;
  font-size: 1rem;
  cursor: pointer;
  min-width: 32px;
  transition: background 0.15s, color 0.15s;
  color: #111;
}
.pagination button.active {
  background: #3d5afe;
  color: #fff;
  border-color: #3d5afe;
}
.pagination button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
.dots {
  padding: 0 8px;
  color: #888;
  font-size: 1.1rem;
}
</style> 