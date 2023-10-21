<template>
    <div id="block" v-show="showBlock" @click="stopTimer">
      Click
    </div>
  </template>
  
  <script>
  export default {
    props: ['delay'],
    data() {
      return {
        showBlock: false,
        timer: null,
        reactionTime: 0
      }
    },
    mounted() {
      setTimeout(() => {
        this.showBlock = true
        this.startTimer()
      }, this.delay)
    },
    methods: {
      startTimer() {
        // start the timer, tick every 10ms
        this.timer = setInterval(() => {
          this.reactionTime += 10
        }, 10)
      },
      stopTimer() {
        // stop the timer
        clearInterval(this.timer)
        this.$emit('end', this.reactionTime)
      }
    }
  }
  </script>

<style lang="postcss" scoped>
    #block {
        @apply w-1/4 lg:w-[250px] rounded-lg bg-sky-400 text-white hover:text-sky-400 hover:bg-white text-center p-5 hover:cursor-pointer
    }
</style>