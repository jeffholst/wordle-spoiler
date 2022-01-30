<script setup lang="ts">
import { ref  } from 'vue'
import WordRow from './components/WordRow.vue'

const showHint = ref(false)
</script>

<template>
  <div class="pt-10 text-center underline text-sky-500">
    <a href="https://www.powerlanguage.co.uk/wordle/">Click here to Play Wordle</a>
  </div>
  
  <WordRow v-if="showHint" class="pt-10"/>
</template>

<style>
</style>
