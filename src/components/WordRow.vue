<script setup lang="ts">
import { ref, watch } from 'vue'
import { GetTodaysWordle } from '../helper'
import LetterBox from './LetterBox.vue'
const solution = ref(GetTodaysWordle())
const answer = ref(["", "", "", "", ""])

const props = defineProps({
    showWordle:{
        type: Boolean,
        default: false
    }
})

const counter = ref(0)

watch(
  () => props.showWordle,
  (newVal, prevVal) => {
    if (newVal) showAnswer()
  }
)

async function showAnswer() {
  for (let loop = 0; loop < 5; loop++)
  { 
      answer.value[loop] = solution.value[loop]
      await new Promise(resolve => setTimeout(resolve, 200));
  }

  for (let loop = 0; loop < 5; loop++)
  { 
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
