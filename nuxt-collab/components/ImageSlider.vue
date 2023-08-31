<template>
  <div class="image-slider">
    <button @click="moveSlider(-1)" class="slider-button prev-button">←</button>
    <div class="slider-container">
      <div
        class="slider-content"
        :style="{ transform: `translateX(-${currentIndex * 100}%)` }"
      >
        <div
          class="slider-item"
          v-for="(image, index) in images"
          :key="index"
        >
          <img :src="image" alt="Slide" />
        </div>
      </div>
    </div>
    <button @click="moveSlider(1)" class="slider-button next-button">→</button>
  </div>
</template>

<script>
export default {
  name: 'ImageSlider',
  data() {
    return {
      images: [
        'img1.png',
        'img2.png',
        'img3.png',
        // Add more image URLs here
      ],
      currentIndex: 0,
    };
  },
  methods: {
    moveSlider(direction) {
      this.currentIndex = (this.currentIndex + direction + this.images.length) % this.images.length;
    },
  },
};
</script>

<style scoped>
.image-slider {
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
}

.slider-container {
  overflow: hidden;
  width: 100%;
}

.slider-content {
  display: flex;
  transition: transform 0.3s ease-in-out;
}

.slider-item {
  flex: 0 0 100%;
  padding: 1rem;
}

.slider-button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(0, 0, 0, 0.5);
  border: none;
  color: white;
  font-size: 1.5rem;
  padding: 0.5rem 1rem;
  cursor: pointer;
}

.prev-button {
  left: 0;
}

.next-button {
  right: 0;
}
</style>
