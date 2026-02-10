<script setup lang="ts">
  import BaseButton from './Button.vue';
</script>

<template>
  <v-dialog max-width="500">
    <template v-slot:activator="{ props: activatorProps }">
      <BaseButton v-bind="activatorProps"/>
    </template>

    <template v-slot:default="{ isActive }">
      <slot name="main" />
    </template>
  </v-dialog>
</template>