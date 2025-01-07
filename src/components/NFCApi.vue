<script setup>
import {ref} from 'vue'

const nfcrecords = ref([])

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
        nfctag.value = event.message.records;
      };
    })
    .catch((error) => {
      alert(`Error! Scan failed to start: ${error}.`);
    });
}

</script>

<template>
 <v-btn color="secondary" @click="scan">Scan</v-btn><br>
  TAGs: <template v-for="row in nfcrecords">{{row}} {{row.mediaType}} {{row.data}}</template>
</template>

<style scoped lang="sass">

</style>
