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
  <div class="flip-card" :class="{bounce: props.showCorrect}">
    <div class="flip-card-inner" :class="{'flipcardtransform' : props.showCorrect}">
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
  width: 50px;
  height: 50px;
  perspective: 1000px;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  font-weight: bold;
  text-align: center;
  font-size: 35px;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  text-transform: capitalize;
}

.flipcardtransform{
    transform: rotateY(180deg)
}

.bounce {
  animation: bounce 2.5s ease 1;
}
@keyframes bounce {
    40% { transform:translateY(0%); }
    50% { transform:translateY(-15%); }
    60% { transform:translateY(0%); }
    70% { transform:translateY(-7%); }
    80% { transform:translateY(0%); }
    90% { transform:translateY(-3%); }
    100% { transform:translateY(0); }
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
  top: -4px;
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
