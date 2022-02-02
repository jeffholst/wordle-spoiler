<script setup lang="ts">
import { ref } from "vue"
import WordRow from "./components/WordRow.vue"
import {ShareNetwork} from 'vue-social-sharing'

const showWordle = ref(false)
var options: any = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' }
const today = ref(new Date().toLocaleDateString("en-US", options))
const wordRow = ref()

const sharing = ref({
  url: 'https://wordle.jeffholst.net',
  title: 'Wordle Spoiler.',
  description: 'Spoil your daily Wordle here.',
  quote: 'Become a Wordle Genius.',
  hashtags: 'wordle,spoiler',
  twitterUser: 'jeffholst'
})

const networks = ref([
  { network: 'email', name: 'Email', icon: 'far fah fa-lg fa-envelope', color: '#333333' },
  { network: 'facebook', name: 'Facebook', icon: 'fab fah fa-lg fa-facebook-f', color: '#1877f2' },
  { network: 'linkedin', name: 'LinkedIn', icon: 'fab fah fa-lg fa-linkedin', color: '#007bb5' },
  { network: 'messenger', name: 'Messenger', icon: 'fab fah fa-lg fa-facebook-messenger', color: '#0084ff' },
  { network: 'reddit', name: 'Reddit', icon: 'fab fah fa-lg fa-reddit-alien', color: '#ff4500' },
  { network: 'skype', name: 'Skype', icon: 'fab fah fa-lg fa-skype', color: '#00aff0' },
  { network: 'sms', name: 'SMS', icon: 'far fah fa-lg fa-comment-dots', color: '#333333' },
  { network: 'twitter', name: 'Twitter', icon: 'fab fah fa-lg fa-twitter', color: '#1da1f2' }
])
</script>

<template>
  <div class="text-center" style="padding-top: 50px">
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
  <div class="pt-10" id="share-network-list">
    <ShareNetwork
      v-for="network in networks"
      :network="network.network"
      :key="network.network"
      :style="{backgroundColor: network.color}"
      :url="sharing.url"
      :title="sharing.title"
      :description="sharing.description"
      :quote="sharing.quote"
      :hashtags="sharing.hashtags"
      :twitterUser="sharing.twitterUser"
    >
      <i :class="network.icon"></i>
      <span>{{ network.name }}</span>
    </ShareNetwork>
  </div>
  <div class="pt-10 text-center underline text-sky-500">
    <a href="https://www.powerlanguage.co.uk/wordle/"
      >Play Wordle</a
    >
  </div>
</template>

<style>

#share-network-list {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  max-width: 1000px;
  margin: auto;
}

a[class^="share-network-"] {
  flex: none;
  color: #FFFFFF;
  background-color: #333;
  border-radius: 3px;
  overflow: hidden;
  display: flex;
  flex-direction: row;
  align-content: center;
  align-items: center;
  cursor: pointer;
  margin: 0 10px 10px 0;
  text-decoration: none;
}

a[class^="share-network-"] .fah {
  background-color: rgba(0, 0, 0, 0.2);
  flex: 0 1 auto;
  margin: 5px;
}

a[class^="share-network-"] span {
  padding: 0 10px;
  flex: 1 1;
  font-weight: 500;
}

a.share-network-twitter {
  background-color: #1da1f2;
}

a.share-network-fakeblock {
  background-color: #41b883;
}

</style>
