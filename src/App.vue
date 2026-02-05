<script setup>
import Countdown from './components/Countdown.vue';

</script>

<template>
  <div id="app">
    <Countdown/>
  </div>
</template>

<style scoped>
#app {
  height: 100vh;
  height: 100dvh;
  display: flex;
  align-items: center;
  justify-content: center;
}
html, body {
  margin: 0;
  height: 100%;
  overflow: hidden;
  position: fixed;
}
body {
  touch-action: none;
}
</style>