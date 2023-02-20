<script setup lang="ts">
// import HelloWorld from './components/HelloWorld.vue'
import { ref, onMounted } from 'vue'

const alphabet = 'abcdefghijklmnopqrstuvwxyz '
const words = ['something', 'anythinggggggg', 'elephant', 'catcatcat', 'brontosaurus', 'panda']
const word = ref()

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

  // set the first word
  word.value = words[0]

  // start the scrambling
  while (true) {

    for (let next_word_idx = 1; next_word_idx < words.length; next_word_idx++) {

      // wait a bit before next word
      await sleep(3000)

      // loop over current word chars
      let next_word = words[next_word_idx]
      let max_length = Math.max(word.value.length, next_word.length)
      for (let idx = 0; idx < max_length; idx++) {

        // slice the alphabet so that it ends at the char that we need
        let alphabet_ = alphabet.slice(0, alphabet.indexOf(next_word[idx]) + 1)

        // exception cut the word if current_word is longer than next_word
        // TODO: arrive at space char by char
        if (idx + 1 > next_word.length) {
          word.value = word.value.slice(0, idx)
        }

        // loop over current char and change update it as per alphabet
        for (let idx_ = 0; idx_ < alphabet_.length; idx_++) {
          await sleep(5)
          word.value = replaceOrAddCharacter(word.value, idx, alphabet_[idx_])
        }
      }
    }
  }
})

</script>

<template>
  {{ word }}
</template>

<style scoped>

</style>
