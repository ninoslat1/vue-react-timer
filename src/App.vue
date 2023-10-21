<template>
  <img src="./assets/logo.png"/>
  <h1 id="welcome">Vue React Time Game</h1>
  <button id="startBtn" @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Result v-if="showResults" :score="score"/>
</template>

<script>
import Block from './components/Block'
import Result from './components/Result'

export default {
  name: 'App',
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
      // set time amount (ms)
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    }
  }
}
</script>

<style lang="postcss">
  * {
    @apply text-center mx-auto my-5 bg-slate-900
  }
  #welcome {
    @apply text-2xl font-bold text-sky-400 py-5;
  }
  #startBtn {
    @apply py-2.5 px-5 rounded-lg bg-sky-400 text-white duration-200 transition-all hover:text-sky-400 hover:bg-white disabled:hidden
  }
</style>
