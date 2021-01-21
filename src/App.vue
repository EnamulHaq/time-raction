<template>
  <div id="app">
    <h1>Ninja reaction timer</h1>
    <button @click="play" :disabled="isPlaying" >Play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <Result v-if="showResult" :score="score" />
  </div>
</template>

<script>
import Block from "@/components/Block";
import Result from "@/components/Result";
export default {
  name: 'App',
  components: {Block, Result},

  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },

  methods: {
    play() {
      this.isPlaying = true
      this.delay = 200 + Math.random() * 5000
      this.showResult = false
    },

    endGame(reactionTime) {
        this.score = parseInt(reactionTime / 60)
        this.isPlaying = false
        this.showResult = true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
