<template>
  <div class="baseBeverage" :style="{ backgroundColor: baseColor }"></div>
</template>

<script>
export default {
  props: {
    baseColor: {
      type: String,
      required: true
    }
  }
}
</script>

<style scoped>
.baseBeverage {
  position: relative;
  width: 100%;
  height: 100%;
  bottom: 0;
  animation: pour-tea 2s;
  z-index: 300;
  transition: background-color 0.5s ease;
}
</style>