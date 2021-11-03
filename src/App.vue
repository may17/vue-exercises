<template>
  <div class="exercise-1 canvas">
    <div class="parkspot-info-wrapper">
      <parkspot-info spot-name="P4" count="1000" />
      <ParkspotInfo spot-name="P3" count="-1" />
      <ParkspotInfo spot-name="P2" count="98" arrow="⮕" />
      <ParkspotInfo spot-name="P1" arrow="⬅" />
    </div>
  </div>
</template>

<script>
import ParkspotInfo from "./components/ParkspotInfo.vue";

export default {
  name: "App",
  components: {
    ParkspotInfo,
  },
};
</script>

<style scoped>
.exercise-1.canvas {
  font-family: Tahoma, Helvetica, sans-serif;
}

.parkspot-info-wrapper {
  background-color: #34495e;
  padding: 10px;
  display: inline-block;
}
</style>
