<template>
  <div>
    <p>Reaction time is: {{score}}</p>
    <p>Rank is: {{rank}}</p>
  </div>
</template>

<script>
export default {
  name: "Result",
  props: ['score'],
  data() {
    return {
      rank: null
    }
  },

  mounted() {
    if (this.score > 40) {
      this.rank = 'Your so lazy'
    } else if (this.score > 20) {
      this.rank = 'Your so fast'
    } else {
      this.rank = 'Supper'
    }
  }
}
</script>

<style scoped>

</style>