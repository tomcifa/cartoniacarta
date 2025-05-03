<script setup>
import moment from 'moment'
import { onBeforeMount, onBeforeUnmount, onMounted, ref } from 'vue'

var birthday = moment('2026-01-28')

let distance = ref()
var distanceInterval

calculateDistance()

function calculateDistance() {
  distance.value = moment.duration(birthday.diff(moment()))
}

onBeforeMount(() => {
  distanceInterval = setInterval(calculateDistance, 1000)
})

onBeforeUnmount(() => {
  clearInterval(distanceInterval)
})

</script>

<template>
  <div id="container">
    <div id="cd_container">
      <h1 id="cd_text">{{ distance.asDays().toFixed() }} days</h1>
      <h1 id="cd_text">{{ distance.hours() }}hrs {{ distance.minutes() }}min {{ distance.seconds() }}sec </h1>
    </div>
  </div>
</template>

<style>
#cd_text {
  font-family: Arial, Helvetica, sans-serif;
  margin:auto;
}

#cd_container {
  
}

#container {
  display: flex;
  flex-direction: row;
  align-items: center;
}
</style>