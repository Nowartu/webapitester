<script setup>
import {ref} from 'vue'

const nfcrecords = ref(['aaa'])

const n = ref(navigator)
alert(navigator)

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
        console.log(event)
        for (const record of event.message.records){
          alert(record.recordType + record.mediaType + record.id)
        }
        nfcrecords.value = event.message.records;
      };
    })
    .catch((error) => {
      alert(`Error! Scan failed to start: ${error}.`);
    });
}

</script>

<template>
 <v-btn color="secondary" @click="scan">Scan</v-btn><br>
  TAGs: <template v-for="row in nfcrecords">{{row}} {{row.data}}</template>
  {{JSON.stringify(n, null, 2)}}
</template>

<style scoped lang="sass">

</style>
