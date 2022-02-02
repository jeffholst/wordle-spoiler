<script setup lang="ts">
import { ref } from "vue";
import WordRow from "./components/WordRow.vue";

const showWordle = ref(false)
var options: any = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' }
const today = ref(new Date().toLocaleDateString("en-US", options))
const wordRow = ref()

</script>

<template>
  <div class="text-center pt-5" style="padding-top: 50px">
    <button
      @click="showWordle = true"
      class="
        bg-blue-500
        hover:bg-blue-700
        text-white
        font-bold
        py-2
        px-4
        rounded
      "
    >
      Spoil Wordle
    </button>
  </div>
  <WordRow class="pt-5" :showWordle="showWordle"/>
  <div class="pt-2 text-center">
    {{ today }} Wordle of the day
  </div>
  <div class="pt-10 text-center underline text-sky-500">
    <a href="https://www.powerlanguage.co.uk/wordle/"
      >Play Wordle</a
    >
  </div>
</template>

<style>
</style>
