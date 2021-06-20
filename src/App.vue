<template>
  <div id="app">
    <Timer 
      @pomodoro="setPredefined(25, 0)"
      @short_break="setPredefined(5, 0)"
      @long_break="setPredefined(15, 0)" 
    />
    <Clock :clock="clock" />
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
* {
    font-family: 'Baloo Tammudu 2';
    font-style: normal;
    font-weight: bold;
    font-size: 36px;
    line-height: 40px;
  }
* button {
  padding: 0.5rem 2rem;
  background: #F5F5FA;
  /* Shadow 3 */

  box-shadow: -5px -5px 10px rgba(255, 255, 255, 0.5), 5px 5px 10px rgba(170, 170, 204, 0.25), 10px 10px 20px rgba(170, 170, 204, 0.5), -10px -10px 20px #FFFFFF;
  border-radius: 15px;
  border: none;
  margin-bottom: 30px;
  margin-left: 20px;
}

* button span {
    font-family: 'Baloo Tammudu 2';
    font-style: normal;
    font-weight: bold;
    font-size: 36px;
    line-height: 40px;
    /* identical to box height, or 111% */

    display: flex;
    align-items: center;
    text-align: center;

    color: #7878AB;
    cursor: pointer;
  }
* button:hover {
  background-color:#E5E5F0;
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
html {
  background-color: #F5F5FA;

}
</style>
