<script setup>
import {ref} from 'vue'

const nfcserialnumber = ref('')


function scan() {
  const ndef = new NDEFReader();
  ndef
    .scan()
    .then(() => {
      ndef.onreadingerror = (event) => {
        alert(
          `Error! Cannot read data from the NFC tag. Try a different one? ${event}`,
        );
      };
      ndef.onreading = (event) => {
        nfcserialnumber.value = event.serialNumber;
      };
    })
    .catch((error) => {
      alert(`Error! Scan failed to start: ${error}.`);
    });
}

</script>

<template>
 <v-btn color="secondary" @click="scan">Scan</v-btn><br>
  Serial Number: {{nfcserialnumber}}<br>
</template>

<style scoped lang="sass">

</style>
