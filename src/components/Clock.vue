<template>
  <div class="clock">
    {{ timer }}
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