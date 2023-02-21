<script setup lang="ts">
import { ref, onMounted } from 'vue'

const word = ref()
const alphabet = 'abcdefghijklmnopqrstuvwxyz '
const words = [
  'machine learning',
  'zero knowledge proofs',
  'blockchains',
  'software development',
]

const sleep = (ms) => {
  return new Promise(resolve => setTimeout(resolve, ms))
}

const replaceOrAddCharacter = (str, idx, repl) => {
  // add
  if (idx > str.length) {
    return str + repl
  }
  // replace
  let start = str.substring(0, idx)
  let end = str.substring(idx + 1, str.length)
  return start + repl + end
}

onMounted( async () => {

  // set the starting string
  word.value = '--//--'

  // start the scrambling
  while (true) {

    for (let next_word_idx = 0; next_word_idx < words.length; next_word_idx++) {

      // loop over current word chars
      let next_word = words[next_word_idx]
      let max_length = Math.max(word.value.length, next_word.length)
      for (let idx = 0; idx < max_length; idx++) {

        // slice the alphabet so that it ends at the char that we need
        let alphabet_ = alphabet.slice(0, alphabet.indexOf(next_word[idx]) + 1)

        // if current word is longer than next word
        // keep the full aphabet with a space at the end
        if (idx + 1 > next_word.length) {
          alphabet_ = alphabet
        }

        // loop over current char and change update it as per alphabet
        for (let idx_ = 0; idx_ < alphabet_.length; idx_++) {
          await sleep(2)
          word.value = replaceOrAddCharacter(word.value, idx, alphabet_[idx_])
        }
      }

      // wait a bit before next word
      await sleep(3000)
    }
  }
})

</script>

<template>
  {{ word }}
</template>

<style scoped>

</style>
