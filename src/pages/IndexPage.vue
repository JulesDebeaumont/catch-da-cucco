<script setup lang="ts">
import { onMounted, ref } from 'vue';
// components
import AnnoyingCucco from 'src/components/AnnoyingCucco.vue';

// consts
const cuccoCount = 20;
const timeAvailable = 60;

// refs
const timer = ref(timeAvailable);
const pointsRef = ref(0);

// functions
function addPoint(points: number) {
  pointsRef.value += points;
}
function timerGoesOn() {
  if (timer.value > 0) {
    setTimeout(() => {
      timer.value = timer.value - 1;
      timerGoesOn();
    }, 1000);
  }
}

// lifeCycle
onMounted(() => {
  timerGoesOn();
});
</script>

<template>
  <div
    class="flex flex-center column"
    style="height: 100vh;"
  >
    <h6 class="q-mt-xs q-pt-xs">
      Catch da cucco ! {{ pointsRef }} {{ timer }}
    </h6>

    <template v-if="timer > 0">
      <div class="flex flex-center column full-width full-height absolute">
        <AnnoyingCucco
          v-for="index in cuccoCount"
          :key="index"
          :isCojiro="index + 1 === cuccoCount"
          @addPoints="addPoint"
        />
      </div>
    </template>

    <template v-else> Bah voilà hein </template>
  </div>
</template>
