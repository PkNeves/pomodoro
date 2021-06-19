<template>
  <div class="timer">
    <button @click="$emit('pomodoro')">Pomodoro</button>
    <button @click="$emit('short_break')">Short Break</button>
    <button @click="$emit('long_break')">Long Break</button>
  </div>
</template>