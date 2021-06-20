<template>
  <div class="timer">
    <button @click="$emit('pomodoro')"><span>Pomodoro</span></button>
    <button @click="$emit('short_break')"><span>Short Break</span></button>
    <button @click="$emit('long_break')"><span>Long Break</span></button>
  </div>
</template>

<style scoped>
  * {
    font-family: 'Baloo Tammudu 2';
    font-style: normal;
    font-weight: bold;
    font-size: 36px;
    line-height: 40px;
  }
  .timer {
    display: flex;
    flex-direction: row;
    justify-content: center;
    margin: 0 10%;
    flex-wrap: wrap;
  }
  button span {
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
  }
</style>