<script setup lang="ts">
import { ref } from 'vue'
import { GetTodaysWordle } from '../helper'

const todaysWorld = ref(GetTodaysWordle())

</script>

<template>
  <h1>Today's Wordle is: {{ todaysWorld }}</h1>

  
</template>

<style scoped>
</style>
