<script setup lang="ts">
import { ref, onMounted } from "vue";
import WordRow from "./components/WordRow.vue";

const showWordle = ref(false);
var options: any = {
  weekday: "long",
  year: "numeric",
  month: "long",
  day: "numeric",
};
const today = ref(new Date().toLocaleDateString("en-US", options));
const wordRow = ref();

onMounted(() => {});

function facebook() {
  let destURL = "https://www.facebook.com/sharer/sharer.php?u=";
  openWindow(destURL);
}

function twitter() {
  let destURL =
    "https://twitter.com/intent/tweet?text=Spoil%20your%20daily%20Wordle.&url=";

  openWindow(destURL);
}

function reddit() {
  let destURL = "https://www.reddit.com/submit?url=";

  openWindow(destURL);
}

function openWindow(destURL: string) {
  let localURL = "https://wordle.jeffholst.net";
  window.open(`${destURL}${localURL}`, "", "width=800,height=600");
}
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
  <WordRow class="pt-5" :showWordle="showWordle" />
  <div class="pt-2 text-center">{{ today }} Wordle of the day</div>

  <div class="pt-5 text-center">
    <div>
      Share on Social Media
    </div>
    <div>
      P.S. Please do not post Wordle Spoilers
    </div>
    <button
      @click="twitter"
      class="
        mt-3
        bg-blue-300
        hover:bg-blue-700
        px-4
        py-2
        font-semibold
        text-white
        inline-flex
        items-center
        space-x-2
        rounded
      "
    >
      <svg
        class="w-5 h-5 fill-current"
        role="img"
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 24 24"
      >
        <path
          d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.17-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"
        />
      </svg>
      <span>Twitter</span>
    </button>

    <button
      @click="facebook"
      class="
        ml-5
        mt-3
        bg-blue-500
        hover:bg-blue-800
        px-4
        py-2
        font-semibold
        text-white
        inline-flex
        items-center
        space-x-2
        rounded
      "
    >
      <svg
        class="w-5 h-5 fill-current"
        role="img"
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 24 24"
      >
        <path
          d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"
        />
      </svg>
      <span>Facebook</span>
    </button>

    <button
      @click="reddit"
      class="
        ml-5
        mt-3
        bg-red-500
        hover:bg-red-700
        px-4
        py-2
        font-semibold
        text-white
        inline-flex
        items-center
        space-x-2
        rounded
      "
    >
      <svg
        class="w-5 h-5 fill-current"
        role="img"
        viewBox="0 0 24 24"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M12 0A12 12 0 0 0 0 12a12 12 0 0 0 12 12 12 12 0 0 0 12-12A12 12 0 0 0 12 0zm5.01 4.744c.688 0 1.25.561 1.25 1.249a1.25 1.25 0 0 1-2.498.056l-2.597-.547-.8 3.747c1.824.07 3.48.632 4.674 1.488.308-.309.73-.491 1.207-.491.968 0 1.754.786 1.754 1.754 0 .716-.435 1.333-1.01 1.614a3.111 3.111 0 0 1 .042.52c0 2.694-3.13 4.87-7.004 4.87-3.874 0-7.004-2.176-7.004-4.87 0-.183.015-.366.043-.534A1.748 1.748 0 0 1 4.028 12c0-.968.786-1.754 1.754-1.754.463 0 .898.196 1.207.49 1.207-.883 2.878-1.43 4.744-1.487l.885-4.182a.342.342 0 0 1 .14-.197.35.35 0 0 1 .238-.042l2.906.617a1.214 1.214 0 0 1 1.108-.701zM9.25 12C8.561 12 8 12.562 8 13.25c0 .687.561 1.248 1.25 1.248.687 0 1.248-.561 1.248-1.249 0-.688-.561-1.249-1.249-1.249zm5.5 0c-.687 0-1.248.561-1.248 1.25 0 .687.561 1.248 1.249 1.248.688 0 1.249-.561 1.249-1.249 0-.687-.562-1.249-1.25-1.249zm-5.466 3.99a.327.327 0 0 0-.231.094.33.33 0 0 0 0 .463c.842.842 2.484.913 2.961.913.477 0 2.105-.056 2.961-.913a.361.361 0 0 0 .029-.463.33.33 0 0 0-.464 0c-.547.533-1.684.73-2.512.73-.828 0-1.979-.196-2.512-.73a.326.326 0 0 0-.232-.095z"
        />
      </svg>
      <span>Reddit</span>
    </button>

    <div class="pt-5">
      Created with 💖 by <a href="https://twitter.com/intent/tweet?screen_name=jeffholst" target="blank" title="@jeffholst">@JeffHolst</a>
    </div>
    <div class="pt-10 text-center underline text-sky-500">
      <a href="https://www.powerlanguage.co.uk/wordle/">Play Wordle</a>
    </div>
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
  background: #213a6f;
}

#fb-share-button svg {
  width: 18px;
  fill: white;
  vertical-align: middle;
  border-radius: 2px;
}

#fb-share-button span {
  vertical-align: middle;
  color: white;
  font-size: 14px;
  padding: 0 3px;
}
</style>
