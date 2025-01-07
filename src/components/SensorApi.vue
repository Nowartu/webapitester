<script setup>
import {ref} from 'vue'

const gyro = ref({
  x: 0,
  y: 0,
  z: 0
})

let gyroscope = new Gyroscope({ frequency: 60 });

gyroscope.addEventListener("reading", () => {
  gyro.value.x = gyroscope.x;
  gyro.value.y = gyroscope.y;
  gyro.value.z = gyroscope.z;

});
gyroscope.start();

</script>

<template>
<h5>Gyroscope</h5>
  x: {{ gyro.x }}<br>
  y: {{ gyro.y }}<br>
  z: {{ gyro.z }}<br>
</template>

<style scoped lang="sass">

</style>
