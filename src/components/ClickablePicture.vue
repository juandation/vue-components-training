<template>
  <img 
    :src="currentImage" 
    :alt="'Clickable picture'" 
    class="clickable-picture"
    @click="toggleImage"
  />
</template>

<script>
export default {
  name: 'ClickablePicture',
  props: {
    img: {
      type: String,
      required: true
    },
    imgClicked: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      isClicked: false
    }
  },
  computed: {
    currentImage() {
      return this.isClicked ? this.imgClicked : this.img;
    }
  },
  methods: {
    toggleImage() {
      this.isClicked = !this.isClicked;
    }
  }
}
</script>

<style scoped>
.clickable-picture {
  cursor: pointer;
  max-width: 200px;
  border-radius: 10px;
  transition: transform 0.1s ease;
}

.clickable-picture:hover {
  transform: scale(1.05);
}

.clickable-picture:active {
  transform: scale(0.95);
}
</style>