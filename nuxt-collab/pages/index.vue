<template>
  <div
    class="waveform-container"
    @mousedown="startDragging"
    @mousemove="handleDragging"
    @mouseup="stopDragging"
    @mouseleave="stopDragging"
  >
    <div
      class="waveform"
      :style="{ transform: `translateX(${position}px)` }"
    ></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dragging: false,
      startPosition: 0,
      currentPosition: 0,
      position: 0,
    };
  },
  methods: {
    startDragging(event) {
      this.dragging = true;
      this.startPosition = event.clientX;
      this.currentPosition = this.position;
    },
    handleDragging(event) {
      if (this.dragging) {
        const deltaX = event.clientX - this.startPosition;
        this.position = this.currentPosition + deltaX;
      }
    },
    stopDragging() {
      this.dragging = false;
    },
  },
};
</script>

<style>
.waveform-container {
  width: 100%;
  height: 100px;
  overflow: hidden;
  position: relative;
  cursor: grab;
}

.waveform {
  width: 200%; /* Make the waveform wider than the container */
  height: 100%;
  background-color: lightblue;
  position: absolute;
  user-select: none;
}
</style>
