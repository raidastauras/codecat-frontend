<script setup lang="ts">
import ScrambleWords from './components/ScrambleWords.vue'
import Cats from './components/Cats.vue'
import { onMounted } from 'vue'

onMounted(() => {
  console.log(`
    Hey there 😼! Just in case you're looking for source code,
    you can find it here: https://github.com/RaidasGrisk/codecat-frontend
  `)
})

</script>

<template>
  <div>

    <div style="font-size: 6em; font-weight: 1000;">
      CodeCat
    </div>

    <div style="font-size: 1em; font-weight: 1000;" class="rainbow">
      <ScrambleWords />
    </div>

    <br>

    <div style="font-size: 2em; font-weight: 1000; color: #54575c;">
      <Cats />
    </div>

  </div>

  <div style="padding-top: 40vh;">
    <a href="https://github.com/RaidasGrisk" target="_blank">github</a><br>
    <a href="https://raidasgrisk.github.io/" target="_blank">portfolio</a><br>
    <a href="" target="">email</a><br>
  </div>

</template>

<style scoped>

@keyframes rainbow {
  0% { color: #29cd64 }
  17% { color: #29cd64 }
  34% { color: #2a7bf5 }
  51% { color: #2af5e4 }
  68% { color: #cd296c }
  85% { color: #f5dd2a }
  100% { color: #29cd64 }
}

.rainbow {
  animation-name: rainbow;
  animation-duration: 30s;
  animation-iteration-count: infinite;
}

</style>
