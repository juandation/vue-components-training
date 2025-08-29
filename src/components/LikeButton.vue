<template>
  <button 
    class="like-button" 
    :style="{ backgroundColor: currentColor }"
    @click="incrementLikes"
  >
    {{ likes }} Likes
  </button>
</template>

<script>
export default {
  name: 'LikeButton',
  data() {
    return {
      likes: 0,
      colors: ['purple', 'blue', 'green', 'yellow', 'orange', 'red']
    }
  },
  computed: {
    currentColor() {
      return this.colors[this.likes % this.colors.length];
    }
  },
  methods: {
    incrementLikes() {
      this.likes++;
    }
  }
}
</script>

<style scoped>
.like-button {
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  color: white;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
}

.like-button:hover {
  opacity: 0.8;
}
</style>