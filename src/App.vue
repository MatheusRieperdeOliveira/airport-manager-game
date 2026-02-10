<script setup lang="ts">
import BaseDialog from './components/base/Dialog.vue';
import FormTask from './components/task/FormTask.vue';

const tasks = [
  {
    "nome": "Joga"
  },
];

</script>

<template>
  <v-card class="bg-purple-darken-1 h-screen rounded-0 pa-1">
    <div class="w-100 d-flex flex-sm-row-reverse mb-1 ">
      <div class="w-auto bg-blue rounded-lg">
        <BaseDialog>
          <template #main>
            <FormTask/>
          </template>
        </BaseDialog>
      </div>
    </div>
    <div class="h-100 w-100">
        <v-row>
          <v-col
              v-for="n in 7"
              :key="n"
              class="d-flex ga-1"
          >
            <v-card class="bg-grey-darken-4 w-100 h-auto pa-1">
              <v-card-title class="text-start text-caption">
                <div class="d-flex align-center justify-space-between">
                  <p>
                    nome do rolê
                  </p>
                  <v-btn
                      size="x-small"
                  />
                </div>
              </v-card-title>
              <!-- corpo -->
              <v-card-item class="bg-grey-darken-3 h-auto rounded-sm">
                <template v-if="true">
                  true
                </template>
                <template v-else>
                  false
                </template>
              </v-card-item>
            </v-card>
          </v-col>
        </v-row>
    </div>
  </v-card>
</template>

<style scoped></style>
