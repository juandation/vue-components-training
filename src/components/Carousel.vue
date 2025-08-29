<template>
  <div class="carousel">
    <button class="carousel-btn left" @click="previousImage">Left</button>
    <img :src="currentImage" alt="Carousel image" class="carousel-image" />
    <button class="carousel-btn right" @click="nextImage">Right</button>
  </div>
</template>

<script>
export default {
  name: 'Carousel',
  props: {
    images: {
      type: Array,
      required: true,
      validator: value => value.length > 0
    }
  },
  data() {
    return {
      currentIndex: 0
    }
  },
  computed: {
    currentImage() {
      return this.images[this.currentIndex];
    }
  },
  methods: {
    nextImage() {
      this.currentIndex = (this.currentIndex + 1) % this.images.length;
    },
    previousImage() {
      this.currentIndex = this.currentIndex === 0 
        ? this.images.length - 1 
        : this.currentIndex - 1;
    }
  }
}
</script>

<style scoped>
.carousel {
  display: flex;
  align-items: center;
  gap: 20px;
  padding: 20px;
}

.carousel-image {
  width: 200px;
  height: 200px;
  object-fit: cover;
  border-radius: 10px;
}

.carousel-btn {
  padding: 10px 15px;
  background: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
}

.carousel-btn:hover {
  background: #0056b3;
}
</style>