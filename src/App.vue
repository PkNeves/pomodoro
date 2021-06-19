<template>
  <div id="app">
    <Timer 
      @pomodoro="setPredefined(25, 0)"
      @short_break="setPredefined(5, 0)"
      @long_break="setPredefined(15, 0)" 
    />
    <Clock :clock="clock"></Clock>
    <ClockControl 
      @start="start()" 
      @pause="pause()"
      @reset="reset($event)" 
    />
  </div>
</template>

<script>
import Clock from '@/components/Clock'
import ClockControl from '@/components/ClockControl'
import Timer from '@/components/Timer'
export default {
  name: 'App',
  components: {
    Clock, ClockControl, Timer
  },
  data() {
    return {
      clock: {
        minute: 25,
        second: 0
      },
      interval: null,
      predefined: {
        minute: 25,
        second: 0
      }
        

    }
  },
  methods: {
    start() {
      if (this.clock.minute > 0) {
        this.interval = setInterval(() => {
          if (this.clock.minute === 0 && this.clock.second === 0) {
            clearInterval(this.interval)
            return
          }
          if (this.clock.second == 0) {
            this.clock.minute -= 1
            this.clock.second = 59
          } else {
            this.clock.second -= 1
          }
        }, 1000)
      }
    },
    pause() {
      this.interval ? clearInterval(this.interval) : this.interval = null
    },
    reset() {
      this.clock.minute = this.predefined.minute
      this.clock.second = this.predefined.second
    },
    setPredefined(minute, second) {
      this.predefined.minute = minute
      this.predefined.second = second
      this.reset()
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
