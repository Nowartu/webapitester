<script setup>
import {ref} from 'vue';

const location = ref({
  longitude: 0,
  latitude: 0,
  accuracy: 0,
})
function success(pos){
  const crd = pos.coords;
  location.value.longitude = crd.longitude;
  location.value.latitude = crd.latitude;
  location.value.accuracy = crd.accuracy;
}
navigator.geolocation.getCurrentPosition(success)
</script>

<template>
  Longitude: {{ location.longitude }}<br>
  Latitude: {{ location.latitude }}<br>
  Accuracy: {{ location.accuracy }}
</template>

<style scoped lang="sass">

</style>
