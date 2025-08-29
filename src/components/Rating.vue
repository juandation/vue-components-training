<template>
  <div class="rating">
    <span v-for="star in stars" :key="star.index" class="star">
      {{ star.filled ? '★' : '☆' }}
    </span>
  </div>
</template>

<script>
export default {
  name: 'Rating',
  props: {
    rate: {
      type: Number,
      required: true,
      validator: value => value >= 0 && value <= 5
    }
  },
  computed: {
    stars() {
      const stars = [];
      for (let i = 1; i <= 5; i++) {
        stars.push({
          index: i,
          filled: i <= Math.round(this.rate)
        });
      }
      return stars;
    }
  }
}
</script>

<style scoped>
.rating {
  font-size: 24px;
  color: #ffd700;
}

.star {
  margin-right: 2px;
}
</style>