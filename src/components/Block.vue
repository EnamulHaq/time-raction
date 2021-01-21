<template>
  <div class="block" v-if="showBlocks" @click="stopTimer">
    Click me
  </div>
</template>

<script>
export default {
  name: "Block",
  props: ['delay'],

  data() {
    return {
      showBlocks: false,
      timer: null,
      reactionTime: 0
    }
  },

  mounted() {
    setTimeout( ()=> {
      this.showBlocks = true
      this.startTimer()
    }, this.delay )
  },

  methods: {
    startTimer() {
      this.timer = setInterval( ()=> {
        this.reactionTime += 10
      }, 10 )
    },
    stopTimer() {
      clearInterval(this.timer)
      this.showBlocks = false
      this.$emit('end', this.reactionTime)
    }
  },
}

</script>

<style scoped>
  .block {
    background: green;
    width: 400px;
    height: 200px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 30px;
    color: #fff;
    margin: 0 auto;
    margin-top: 30px;

  }
</style>