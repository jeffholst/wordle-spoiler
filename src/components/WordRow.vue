<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { GetTodaysWordle } from '../helper'
import LetterBox from './LetterBox.vue'
const solution = ref(GetTodaysWordle())
const answer = ref(["", "", "", "", ""])

const counter = ref(0)

onMounted (() => {showAnswer()})

async function showAnswer() {
  for (let loop = 0; loop < 5; loop++)
  { 
      answer.value[loop] = solution.value[loop]
      await new Promise(resolve => setTimeout(resolve, 500));
      counter.value++
      await new Promise(resolve => setTimeout(resolve, 200));
  }
}


</script>

<template>
  <div class="grid max-w-xs grid-cols-5 gap-1 mx-auto mb-1">
    <letter-box v-for="i in 5" :key="i" :letter="answer[i-1]" :showCorrect="counter >= i" />
  </div>
</template>

<style scoped>
</style>
