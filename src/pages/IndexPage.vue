<script setup lang="ts">
// components
import AnnoyingCucco from 'src/components/AnnoyingCucco.vue';
import { ref } from 'vue';

// consts
const cuccoCount = 20;

// refs
const timer = ref(30);
const pointsRef = ref(0);

// functions
function addPoint(points: number) {
  pointsRef.value += points;
}
</script>

<template>
  <div
    class="flex flex-center column"
    style="height: 100vh; padding-bottom: 300px"
  >
    <h6 class="q-mt-xs q-pt-xs">Catch da cucco ! {{ pointsRef }}</h6>

    <AnnoyingCucco
      v-for="index in cuccoCount"
      :key="index"
      :isCojiro="index + 1 === cuccoCount"
      @addPoints="addPoint"
    />
  </div>
</template>
