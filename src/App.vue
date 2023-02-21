<script setup lang="ts">
import ScrambleWords from './components/ScrambleWords.vue'
import Cats from './components/Cats.vue'

</script>

<template>
  <div>

    <div style="font-size: 6em; font-weight: 1000;">
      CodeCat
    </div>

    <div style="font-size: 1em; font-weight: 1000; color: #763ae7;">
      <ScrambleWords />
    </div>

    <br>

    <div style="font-size: 2em; font-weight: 1000; color: #54575c;">
      {{ '[' }} <Cats /> {{ ']' }}
    </div>

  </div>

  <div style="padding-top: 40vh;">
    <a style="color: #54575c;" href="https://github.com/RaidasGrisk" target="_blank">github</a><br>
    <a style="color: #54575c;" href="https://raidasgrisk.github.io/" target="_blank">portfolio</a><br>
    <a style="color: #54575c;">email</a><br>
  </div>

</template>

<style scoped>
</style>
