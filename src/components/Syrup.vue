<template>
  <div class="syrup" :style="{ backgroundColor: syrupColor }"></div>
</template>

<script>
export default {
  props: {
    syrupColor: {
      type: String,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
.syrup {
  transform: translateY(400%);
  background-color: #c6c6c6;
  position: relative;
  width: 100%;
  height: 20%;
  animation: pour-tea 2s 1s forwards;
  z-index: 2;
  transition: background-color 0.5s ease;
}
</style>