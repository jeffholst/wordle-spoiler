<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps({
  letter: {
    type: String,
    default: ",",
  },
  showCorrect: {
    type: Boolean,
    default: false,
  },
});

const style = computed(() => props.showCorrect ? 'transform: rotateY(180deg)' : '')
</script>

<template>
  <div class="flip-card" >
    <div class="flip-card-inner" :style="style">
      <div class="flip-card-front">
        <div class="letterbox">
          {{ letter }}
        </div>
      </div>
      <div class="flip-card-back">
        <div class="letterbox">
          {{ letter }}
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.flip-card {
  background-color: transparent;
  width: 60px;
  height: 60px;
  perspective: 1000px;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  font-weight: bold;
  text-align: center;
  font-size: 40px;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  text-transform: capitalize;
}

.flipcardtransform{
    transform: rotateY(180deg)
}



.flip-card-front,
.flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.letterbox {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0px;
}

.flip-card-front {
  color: #d7dadc;
  border: 2px solid grey;
  border-radius: 5px;
}

.flip-card-back {
  background-color: #538d4e;
  color: white;
  border: 2px solid #538d4e;
  border-radius: 5px;
  transform: rotateY(180deg);
}
</style>
