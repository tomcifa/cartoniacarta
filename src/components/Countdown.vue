<script setup>
import moment from 'moment'
import { onBeforeMount, onBeforeUnmount, onMounted, ref } from 'vue'

var birthdate = moment('2008-01-28')

let distance = ref()
var distanceInterval

calculateDistance()

function calculateDistance() {
  distance.value = -moment.duration(birthdate.diff(moment()))
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
    <h1 id="cd_text">{{ Math.floor(distance.asYears()) }}anni {{ Math.floor(distance.asDays()) }} giorni</h1>
    <h1 id="cd_text">{{ distance.hours() }}hrs {{ distance.minutes() }}min {{ distance.seconds() }}sec </h1>
  </div> 
</template>

<style>
#cd_text {
  font-family: Arial, Helvetica, sans-serif;
  margin:auto;
  user-select: none;
}

#cd_container {
  
}

#container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>