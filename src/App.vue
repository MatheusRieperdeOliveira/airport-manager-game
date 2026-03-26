<script setup lang="ts">
import Airport from './components/base/Airport.vue';
import { ref } from 'vue';
import Plane from './components/base/Plane.vue';

type PlaneState = 'flying' | 'landing' | 'taxiing';
const planeState = ref<PlaneState>('flying');

const nextState = () => {
  if (planeState.value === 'flying') {
    planeState.value = 'landing';
  } else if (planeState.value === 'landing') {
    planeState.value = 'taxiing';
  } else {
    planeState.value = 'flying';
  }
};
</script>

<template>
  <v-card class="bg-light-blue h-screen rounded-0 pa-1 d-flex justify-center align-center">
    <v-btn class="position-absolute" style="top: 20px; z-index: 100;" color="primary" @click="nextState">
      Avançar Étapa: {{ planeState.toUpperCase() }}
    </v-btn>
    <Airport />
    <Plane :state="planeState"/>
  </v-card>
</template>

<style scoped></style>
