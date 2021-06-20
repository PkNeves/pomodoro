<template>
  <div class="clockControl">
    <button @click="$emit('start')"><span class='start'>Start</span></button>
    <button @click="$emit('pause')"><span class='pause'>Pause</span></button>
    <button @click="$emit('reset')"><span class='reset'>Reset</span></button>
  </div>
</template>
<script>
  export default {
  }
</script>
<style scoped>
  .clockControl {
    display: flex;
    flex-direction: row;
    justify-content: center;
    margin: 0 10%;
    flex-wrap: wrap;
    margin-top: 30px;

  }
  .start {
    color: #78ab78;
  }
  .reset {
    color: #ab7878;
  }
</style>