<script setup>
import {ref} from 'vue'

const battery = ref({
  charging: null,
  chargingTime: null,
  dischargingTime: null,
  level: null
})

navigator.getBattery().then(b => {
  battery.value.charging = b.charging;
  battery.value.chargingTime = b.chargingTime;
  battery.value.dischargingTime = b.dischargingTime;
  battery.value.level = b.level;
})
</script>

<template>
  Charging: {{ battery.charging }} <br>
  ChargingTime: {{ battery.chargingTime }} <br>
  DischargingTime: {{ battery.dischargingTime }} <br>
  Level: {{ battery.level }}
</template>

<style scoped lang="sass">

</style>
