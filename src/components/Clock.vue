<template>
  <div class="clock">
    <p>{{ timer }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      timer: `${this.clock.minute}:${this.clock.second}`
    }
  },
  props: {
    clock: Object
  },

  watch: {
    clock: {
      deep: true,
      handler() {
        let minute = this.clock.minute < 10 ? '0'+this.clock.minute : this.clock.minute
        let second = this.clock.second < 10 ? '0'+this.clock.second : this.clock.second
        this.timer = `${minute}:${second}`
      },
      immediate() {
        let minute = this.clock.minute < 10 ? '0'+this.clock.minute : this.clock.minute
        let second = this.clock.second < 10 ? '0'+this.clock.second : this.clock.second
        this.timer = `${minute}:${second}`
      }
    }
  }
}
</script>

<style scoped>
  p {
    font-size: 5em;
    margin: 0;
    font-weight: 700;
    color: #7878AB;
  }
  .clock {
    margin: 0 10%;
  }
  @media screen and (max-width: 800px) {
    p {
      font-size: 3em;
      margin: 0;
    }
  }
</style>