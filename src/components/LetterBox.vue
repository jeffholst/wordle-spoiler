<script setup lang="ts">
    const props = defineProps({
        letter: {
            type: String,
            default: ","
        },
        showCorrect:{
            type: Boolean,
            default: false
        }
    })
</script>

<template>
  <div class="col-span-1 flex items-center justify-center h-16 uppercase border-2 border-gray-200"
    :class="{'border-green-600 bg-green-600 text-white' : showCorrect}">
      {{ letter}}
  </div>
</template>

<style scoped>
</style>
