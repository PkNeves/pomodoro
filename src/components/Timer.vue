<template>
  <div class="timer flex-container">
    <button @click="$emit('pomodoro')"><span>Pomodoro</span></button>
    <button @click="$emit('short_break')"><span>Short Break</span></button>
    <button @click="$emit('long_break')"><span>Long Break</span></button>
  </div>
</template>

<style scoped>
  .timer {
    display: flex;
    flex-direction: row;
    justify-content: center;
    margin: 0 10%;
    flex-wrap: nowrap;
  }
  @media screen and (max-width: 800px) {
    button {
      padding: 0.4rem 1rem;
    }
    button span{
      font-size: 0.55em;
    }
    .timer {
      justify-content: space-between;
    }
  }
   @media screen and (max-width: 600px) {
    button {
      padding: 0.1rem 0.4rem;
      margin: 0;
    }
    button span{
      font-size: 0.4em;
    }
  }
  @media screen and (max-width: 400px) {
    button {
      padding: 0.4rem 0.45rem;
      margin: 0;
    }
    button span{
      font-size: 0.3em;
      line-height: 0.3rem;
    }
  }
  @media screen and (max-width: 370px) {
    button {
      padding: 0.3rem 0.45rem;
      margin: 0;
    }
    button span{
      font-size: 0.24em;
      line-height: 0.24rem;
    }
  }
  
</style>