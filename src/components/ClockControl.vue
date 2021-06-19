<template>
  <div class="clockControl">
    <button @click="$emit('start')">Start</button>
    <button @click="$emit('pause')">Pause</button>
    <button @click="$emit('reset')">Reset</button>
  </div>
</template>
<script>
  export default {
  }
</script>