<script setup>
import {ref} from 'vue'

const type = ref('null')
const angle = ref(0)

screen.orientation.addEventListener('change', (event) => {
  type.value = event.target.value
  angle.value = event.target.angle
})
</script>

<template>
  Type: {{type}} <br>
  Screen Angle: {{angle}}
</template>

<style scoped lang="sass">

</style>
