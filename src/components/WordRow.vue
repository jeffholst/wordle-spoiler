<script setup lang="ts">
import { ref, watch } from 'vue'
// @ts-ignore
import { GetTodaysWordle5,  GetTodaysWordle6} from '../helper'
import LetterBox from './LetterBox.vue'



const props = defineProps({
    showWordle:{
        type: Boolean,
        default: false
    },
    wordleLength:{
        type: Number,
        default: 5
    }
})

const solution = ref(props.wordleLength === 5 ? GetTodaysWordle5() : GetTodaysWordle6())
const answer = ref(props.wordleLength === 5 ? ["", "", "", "", ""] : ["", "", "", "", "", ""])

const counter = ref(0)

watch(
  () => props.showWordle,
  (newVal, prevVal) => {
    if (newVal) showAnswer()
  }
)

async function showAnswer() {
  for (let loop = 0; loop < props.wordleLength; loop++)
  { 
      answer.value[loop] = solution.value[loop]
      await new Promise(resolve => setTimeout(resolve, 200));
  }

  for (let loop = 0; loop < props.wordleLength; loop++)
  { 
      counter.value++
      await new Promise(resolve => setTimeout(resolve, 125));
  }
  
}


</script>

<template>
  <div class="grid max-w-xs gap-1 mx-auto mb-1" :class="{'grid-cols-5': props.wordleLength === 5, 'grid-cols-6': props.wordleLength === 6}">
    <letter-box v-for="i in props.wordleLength" :key="i" :letter="answer[i-1]" :showCorrect="counter >= i" />
  </div>
</template>

<style scoped>
</style>
