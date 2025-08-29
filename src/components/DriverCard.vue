<template>
  <div class="driver-card">
    <div class="driver-info">
      <img :src="img" :alt="name" class="driver-image" />
      <div class="driver-details">
        <h3 class="driver-name">{{ name }}</h3>
        <Rating :rate="rating" />
        <p class="car-info">{{ car.model }} - {{ car.licensePlate }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import Rating from './Rating.vue'

export default {
  name: 'DriverCard',
  components: {
    Rating
  },
  props: {
    name: {
      type: String,
      required: true
    },
    rating: {
      type: Number,
      required: true,
      validator: value => value >= 0 && value <= 5
    },
    img: {
      type: String,
      required: true
    },
    car: {
      type: Object,
      required: true,
      validator: value => value.model && value.licensePlate
    }
  }
}
</script>

<style scoped>
.driver-card {
  background: #455eb5;
  color: white;
  border-radius: 10px;
  padding: 20px;
  margin: 10px;
  width: 500px;
}

.driver-info {
  display: flex;
  align-items: center;
}

.driver-image {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  object-fit: cover;
  margin-right: 20px;
}

.driver-details {
  flex: 1;
}

.driver-name {
  margin: 0 0 10px 0;
  font-size: 24px;
  font-weight: bold;
}

.car-info {
  margin: 10px 0 0 0;
  font-size: 16px;
}
</style>