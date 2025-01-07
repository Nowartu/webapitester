<script setup>
import {shallowRef} from 'vue';
import HomePage from "@/components/HomePage.vue";
import GeolocationComponent from "@/components/GeolocationComponent.vue";
import BatteryApi from "@/components/BatteryApi.vue";
import NetworkApi from "@/components/NetworkApi.vue";
import VibrationApi from "@/components/VibrationApi.vue";
import ScreenOrientation from "@/components/ScreenOrientation.vue";
import SensorApi from "@/components/SensorApi.vue";

const comp = shallowRef(HomePage)
</script>

<template>
  <v-layout>
    <v-navigation-drawer
      permanent
      expand-on-hover
      rail
    >
      <v-list density="compact" nav>
        <v-list-item prepend-icon="mdi-earth" title="Geolocation" @click="comp=GeolocationComponent"></v-list-item>
        <v-list-item prepend-icon="mdi-battery" title="Battery" @click="comp=BatteryApi"></v-list-item>
        <v-list-item prepend-icon="mdi-wifi" title="Network" @click="comp=NetworkApi"></v-list-item>
        <v-list-item prepend-icon="mdi-screen-rotation" title="Screen" @click="comp=ScreenOrientation"></v-list-item>
        <v-list-item prepend-icon="mdi-leak" title="Sensor" @click="comp=SensorApi"></v-list-item>
        <v-list-item prepend-icon="mdi-vibrate" title="Vibration" @click="comp=VibrationApi"></v-list-item>
        <v-list-item prepend-icon="mdi-nfc" title="NFC" @click="comp=GeolocationComponent"></v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main style="height: 250px">
      <v-container class="text-center">
        <component :is="comp" />
      </v-container>
    </v-main>
  </v-layout>
</template>

<style scoped lang="sass">

</style>
