<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const cat = ref('🐱‍💻')
const cats = [
  '🐈',
  '🐱',
  '😿',
  '🙀',
  '😾',
  '😹',
  '😼',
  '😺',
  '😽',
  '😸',
  '🐈‍⬛',
  '😻',
  '🐱‍🚀',
  '🐱‍👤',
  '🐱‍💻',
  '🐱‍🐉',
  '🐱‍👓',
  '🐱‍🏍',
  '🐾',
  '🦊',
  '🦁',
  '🐯',
  '🐅',
  '🐆',
]

const randomizeCat = () => {
  cat.value = cats[Math.floor(Math.random()*cats.length)]
}

onMounted(() => {
  window.addEventListener('wheel', (event) => {
    randomizeCat()
  })
  window.addEventListener('keypress', (event) => {
    randomizeCat()
  })
})

onUnmounted(() => {
  window.removeEventListener('wheel', (event) => {
    randomizeCat()
  })
  window.removeEventListener('keypress', (event) => {
    randomizeCat()
  })
})

</script>

<template>
  {{ cat }}
</template>

<style scoped>

</style>
