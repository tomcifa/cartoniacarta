<script setup>
import moment from 'moment'
import { onBeforeMount, onBeforeUnmount, onMounted, ref } from 'vue'

var birthdate = moment('2008-01-28')

let age = ref()
var distanceInterval

calculateDistance()

function calculateDistance() {
  const now = moment()

  const years = now.diff(birthdate, 'years')
  const months = now.diff(birthdate.clone().add(years, 'years'), 'months')
  const days = now.diff(birthdate.clone().add(years, 'years').add(months, 'months'), 'days')
  const hours = now.diff(birthdate.clone().add(years, 'years').add(months, 'months').add(days, 'days'), 'hours')
  const minutes = now.diff(birthdate.clone().add(years, 'years').add(months, 'months').add(days, 'days').add(hours, 'hours'), 'minutes')
  const seconds = now.diff(birthdate.clone().add(years, 'years').add(months, 'months').add(days, 'days').add(hours, 'hours').add(minutes, 'minutes'), 'seconds')

  age.value = { years, months, days, hours, minutes, seconds }
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
    <h1 id="cd_text">{{ age.years }}yrs {{ age.days }}days</h1>
    <h1 id="cd_text">{{ age.hours }}hrs {{ age.minutes }}min {{ age.seconds }}sec </h1>
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