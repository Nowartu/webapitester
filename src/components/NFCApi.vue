<script setup>

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
        alert(`NDEF message read. ${event}`);
      };
    })
    .catch((error) => {
      alert(`Error! Scan failed to start: ${error}.`);
    });
}

</script>

<template>
 <v-btn color="secondary" @click="scan">Scan</v-btn>
</template>

<style scoped lang="sass">

</style>
