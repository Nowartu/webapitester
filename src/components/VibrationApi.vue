<script setup>

function vibrate() {
  navigator.vibrate(50)
}

</script>

<template>
  <v-btn color="secondary" @click="vibrate()">Zawibruj</v-btn>
</template>

<style scoped lang="sass">

</style>
