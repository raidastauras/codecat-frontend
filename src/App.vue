<script setup lang="ts">
import ScrambleWords from './components/ScrambleWords.vue'
import Cats from './components/Cats.vue'
import { onMounted } from 'vue'
import { useIsMobile } from './utils'
import { NButton, NTooltip } from 'naive-ui'

const isMobile = useIsMobile()

const copyToClipboard = () => {
  navigator.clipboard.writeText('raidas@codecat.cloud')
}

onMounted(() => {
  console.log(`
    Hey there 😼! Just in case you're looking for source code,
    you can find it here: https://github.com/RaidasGrisk/codecat-frontend
  `)
})

</script>

<template>
  <div :style="isMobile ? 'padding: 5em 2em 5em 2em' : 'padding: 5em 5em 5em 5em'">
    <div>
      <div :style="isMobile ? 'font-size: 4em; font-weight: 1000;' : 'font-size: 6em; font-weight: 1000;'">
        CodeCat
      </div>
      <div :style="isMobile ? 'font-size: 1.5em; font-weight: 1000;' : 'font-size: 2em; font-weight: 1000;'" class="rainbow">
        <ScrambleWords />
      </div>
      <br>
      <div :style="isMobile ? 'font-size: 2em; font-weight: 1000; color: #54575c;' : 'font-size: 3em; font-weight: 1000; color: #54575c;'">
        <Cats />
      </div>
    </div>
    <div style="padding-top: 50%;">
      <a href="https://github.com/RaidasGrisk" target="_blank">github</a><br>
      <a href="https://raidasgrisk.github.io/" target="_blank">portfolio</a><br>
      <span>
        <n-tooltip placement="bottom" trigger="click" :show-arrow="false">
          <template #trigger>
            <a @click="copyToClipboard()" style="cursor: pointer;">
              email
            </a>
          </template>
          <span> Copied! </span>
        </n-tooltip>
      </span>
    </div>
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
