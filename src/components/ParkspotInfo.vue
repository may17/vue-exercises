<template>
  <div v-if="displaySpot" class="parkspot-info" :class="optionalStyling">
    <div class="parkspot-info__arrow">{{ arrow }}</div>
    <div class="parkspot-info__free-spaces">
      <span class="parkspot-info__count">{{ paddedCount }}</span>
      <span class="parkspot-info__count-label">Freie Plätze</span>
    </div>
    <div class="parkspot-info__name">{{ spotName }}</div>
  </div>
</template>

<script>
export default {
  name: "ParkspotInfo",
  props: {
    arrow: {
      type: String,
      default: "⬆",
    },
    count: {
      type: String,
      default: "0",
    },
    spotName: {
      type: String,
      required: true,
    },
  },
  computed: {
    optionalStyling() {
      let returnValue = "";

      if (this.count < 9 && this.count > 0) {
        returnValue = "parkspot-info--few";
      } else if (this.count === "0") {
        returnValue = "parkspot-info--out";
      }

      return returnValue;
    },
    displaySpot() {
      return this.count >= 0 && this.count <= 999;
    },
    paddedCount() {
      return this.count.padStart(3, "0");
    },
  },
};
</script>

<style scoped>
.parkspot-info {
  background-color: #3498db;
  color: #fff;
  width: 600px;
  display: flex;
  width: 380px;
  justify-content: center;
  align-items: center;
  padding: 0 40px;
  border: 2px solid #fff;
}

.parkspot-info--few {
  background-color: #f9ca24;
}

.parkspot-info--out {
  background-color: #eb4d4b;
}

.parkspot-info__arrow {
  font-size: 5rem;
}

.parkspot-info__free-spaces {
  margin: 0 40px;
}

.parkspot-info__count {
  font-family: Tahoma, Helvetica, sans-serif;
  display: block;
  font-size: 2.9rem;
  background-color: #34495e;
  color: #fff200;
  padding: 0px 0px 0px 5px;
  text-align: center;
  letter-spacing: 0.5rem;
}

.parkspot-info__count-label {
  display: block;
  text-align: center;
}

.parkspot-info__name {
  font-weight: bold;
  font-size: 7rem;
}
</style>