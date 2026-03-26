<script setup lang="ts">


</script>

<template>
  <v-card 
    class="position-relative bg-grey-darken-4 rounded-0 pa-0 d-flex align-center justify-center elevation-5 border-t border-b border-grey-darken-2" 
    style="width: 80%; height: 180px; max-width: 1200px;"
  >
    <div class="d-flex w-100 justify-space-around align-center" style="padding: 0 15%;">
      <div
        v-for="n in 10"
        :key="n"
        class="bg-yellow-lighten-2"
        style="width: 5%; height: 8px; border-radius: 4px;"
      ></div>
    </div>

    <div class="position-absolute d-flex flex-column justify-center align-center h-100 py-3" style="left: 20px; gap: 8px;">
        <div v-for="n in 8" :key="'start-'+n" class="bg-white" style="width: 30px; height: 8px;"></div>
    </div>
    
    <div class="position-absolute text-white font-weight-bold" style="left: 80px; font-size: 38px; transform: rotate(90deg);">
      24
    </div>

    <div class="position-absolute d-flex flex-column justify-center align-center h-100 py-3" style="right: 20px; gap: 8px;">
        <div v-for="n in 8" :key="'end-'+n" class="bg-white" style="width: 30px; height: 8px;"></div>
    </div>

    <div class="position-absolute text-white font-weight-bold" style="right: 80px; font-size: 38px; transform: rotate(-90deg);">
      06
    </div>
  </v-card>
</template>

<style scoped></style>
