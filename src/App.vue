<script setup lang="ts">
import { ref, onMounted } from "vue";
import WordRow from "./components/WordRow.vue";

const showWordle = ref(false)
var options: any = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' }
const today = ref(new Date().toLocaleDateString("en-US", options))
const wordRow = ref()

onMounted(() => {
var fbButton:any  = document.getElementById('fb-share-button');
var url = 'https://wordle.jeffholst.net'

fbButton.addEventListener('click', function() {
    window.open('https://www.facebook.com/sharer/sharer.php?u=' + url,
        'facebook-share-dialog',
        'width=800,height=600'
    );
    return false;
});
})

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
  <a class="twitter-share-button"
  href="https://twitter.com/intent/tweet?text=Spoil%20your%20daily%20Wordle.&url=https://wordle.jeffholst.net"
  data-size="large">
Tweet</a>

<div id="fb-share-button">
    <svg viewBox="0 0 12 12" preserveAspectRatio="xMidYMid meet">
        <path class="svg-icon-path" d="M9.1,0.1V2H8C7.6,2,7.3,2.1,7.1,2.3C7,2.4,6.9,2.7,6.9,3v1.4H9L8.8,6.5H6.9V12H4.7V6.5H2.9V4.4h1.8V2.8 c0-0.9,0.3-1.6,0.7-2.1C6,0.2,6.6,0,7.5,0C8.2,0,8.7,0,9.1,0.1z"></path>
    </svg>
    <span>Share</span>
</div>

</template>

<style>
#fb-share-button {
    background: #3b5998;
    border-radius: 3px;
    font-weight: 600;
    padding: 5px 8px;
    display: inline-block;
    position: static;
}

#fb-share-button:hover {
    cursor: pointer;
    background: #213A6F
}

#fb-share-button svg {
    width: 18px;
    fill: white;
    vertical-align: middle;
    border-radius: 2px
}

#fb-share-button span {
    vertical-align: middle;
    color: white;
    font-size: 14px;
    padding: 0 3px
}
</style>
