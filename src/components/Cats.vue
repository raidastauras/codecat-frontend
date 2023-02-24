<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'
import { NSpace } from 'naive-ui'
import { useIsMobile } from '../utils'

const isMobile = useIsMobile()
const prevYTouch = ref(0)
const transition = ref(true)
const cat = ref('')
const cats = [
  '🐱',
  // '😿',
  '🙀',
  '😾',
  '😹',
  '😼',
  '😺',
  '😽',
  '😸',
  '😻',
  '🦁',
  '🐯',

  // '🐈‍⬛',
  // '🐈',
  // '🐅',
  // '🐆',

  // '🐱‍🚀',
  // '🐱‍👤',
  // '🐱‍💻',
  // '🐱‍🐉',
  // '🐱‍👓',
  // '🐱‍🏍',
  // '🐾',
  // '🦊',
]

const sleep = (ms: number) => {
  return new Promise(resolve => setTimeout(resolve, ms))
}

const randomizeCat = async () => {
  transition.value = !transition.value
  cat.value = cats[Math.floor(Math.random()*cats.length)]
  await sleep(100)
  transition.value = !transition.value
}

onMounted( async() => {
  await randomizeCat()

  // wheel
  window.addEventListener('wheel', async (event) => {
    await randomizeCat()
  })

  // button push
  window.addEventListener('keypress', async (event) => {
    await randomizeCat()
  })

  // click
  window.addEventListener('click', async (event) => {
    await randomizeCat()
  })

  // mobile (also try to add some kind of a threshold)
  window.addEventListener('touchmove', async (event) => {
    const yTouch = event.changedTouches[0].clientY
    if (Math.abs(prevYTouch.value - yTouch) > 100) {
      await randomizeCat()
      prevYTouch.value = yTouch
    }
  })
})

// repeat the same as onMounted, but remove
onUnmounted( async() => {
  window.removeEventListener('wheel', async (event) => {
    await randomizeCat()
  })
  window.removeEventListener('keypress', async (event) => {
    await randomizeCat()
  })
  window.removeEventListener('click', async (event) => {
    await randomizeCat()
  })
  window.removeEventListener('touchmove', async (event) => {
    await randomizeCat()
  })
  window.removeEventListener('touchmove', async (event) => {
    const yTouch = event.changedTouches[0].clientY
    if (Math.abs(prevYTouch.value - yTouch) > 100) {
      await randomizeCat()
      prevYTouch.value = yTouch
    }
  })
})

</script>

<template>
  <n-space justify="center">
    <span>[</span>
    <Transition name="slide-fade" :style="isMobile ? 'position:relative; bottom: 30px' : 'position:relative; bottom: 40px'">
      <p v-if="transition">{{ cat }}</p>
    </Transition>
    <span>]</span>
  </n-space>
</template>

<style>

/* https://vuejs.org/guide/built-ins/transition.html#css-based-transitions */
.slide-fade-enter-active {
  transition: all 0.1s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.1s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from {
  transform: translateY(-10px);
  opacity: 0;
}
.slide-fade-leave-to {
  transform: translateY(10px);
  opacity: 0;
}

</style>
