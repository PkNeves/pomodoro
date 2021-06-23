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
    <Footer />
  </div>
</template>

<script>
import Clock from '@/components/Clock'
import ClockControl from '@/components/ClockControl'
import Timer from '@/components/Timer'
import Footer from '@/components/Footer'
export default {
  name: 'App',
  components: {
    Clock, ClockControl, Timer, Footer
  },
  mounted () {
    this.ring = new Audio("http://soundbible.com/mp3/Elevator Ding-SoundBible.com-685385892.mp3")
  },
  data() {
    return {
      ring: '',
      clock: {
        minute: 25,
        second: 0
      },
      interval: undefined,
      predefined: {
        minute: 25,
        second: 0
      }
        

    }
  },
  methods: {
    start() {
      if (this.interval !== undefined || this.clock.minute <= 0) return
      // if (this.clock.minute > 0) {
        this.interval = setInterval(() => {
          if (this.clock.minute === 0 && this.clock.second === 0) {
            this.interval = clearInterval(this.interval)
            this.ring.play()
            return
          }
          if (this.clock.second == 0) {
            this.clock.minute -= 1
            this.clock.second = 10
          } else {
            this.clock.second -= 1
          }
        }, 1000)
      // }
    },
    pause() {
      this.interval = clearInterval(this.interval)
    },
    reset() {
      this.clock.minute = this.predefined.minute
      this.clock.second = this.predefined.second
      this.interval = clearInterval(this.interval)

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
    font-family: Goudy Bookletter 1911, sans-serif;
    font-style: normal;
    font-weight: bold;
    font-size: 36px;
  }
* button {
  padding: 0.4rem 1.4rem;
  background: #F5F5FA;
  /* Shadow 3 */

  box-shadow: -5px -5px 10px rgba(255, 255, 255, 0.5), 5px 5px 10px rgba(170, 170, 204, 0.25), 10px 10px 20px rgba(170, 170, 204, 0.5), -10px -10px 20px #FFFFFF;
  border-radius: 15px;
  border: none;
  margin-bottom: 30px;
  margin-left: 20px;
  cursor: pointer;
}

* button span {
    font-size: 26px;
    line-height: 42px;
    /* identical to box height, or 111% */

    display: flex;
    align-items: center;
    text-align: center;

    color: #7878AB;
  }
* button:hover {
  background-color:#E5E5F0;
}
#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
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
