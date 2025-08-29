<template>
  <div class="id-card">
    <div class="id-card__image">
      <img :src="picture" :alt="`${firstName} ${lastName}`" @error="handleImageError" />
    </div>
    <div class="id-card__info">
      <div class="id-card__name">
        <div><strong>First name:</strong> {{  }}</div>
        <div><strong>Last name:</strong> {{ lastName }}</div>
      </div>
      <div class="id-card__details">
        <div><strong>Gender:</strong> {{ gender }}</div>
        <div><strong>Height:</strong> {{ height }}cm</div>
        <div><strong>Birth:</strong> {{ formattedBirthDate }}</div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'


const props = defineProps({
  lastName: {
    type: String,
    required: true
  },
  firstName: {
    type: String,
    required: true
  },
  gender: {
    type: String,
    required: true,
    validator: (value) => ['male', 'female'].includes(value)
  },
  height: {
    type: Number,
    required: true
  },
  birth: {
    type: Date,
    required: true
  },
  picture: {
    type: String,
    required: true
  }
})


const formattedBirthDate = computed(() => {
  return props.birth.toDateString()
})


const handleImageError = (event) => {
  console.warn('Failed to load profile image:', props.picture)
  // Could add fallback image logic here in future tasks
}
</script>

<style scoped>
.id-card {
  display: flex;
  border: 2px solid var(--color-border, #ddd);
  border-radius: 8px;
  padding: 20px;
  margin: 10px 0;
  background: var(--color-background, #fff);
  max-width: 500px;
  font-family: var(--font-family, Arial, sans-serif);
}

.id-card__image {
  flex-shrink: 0;
  width: 150px;
  margin-right: 20px;
}

.id-card__image img {
  width: 100%;
  height: auto;
  border-radius: 4px;
  object-fit: cover;
}

.id-card__info {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.id-card__name {
  margin-bottom: 15px;
}

.id-card__name div,
.id-card__details div {
  margin-bottom: 5px;
}

.id-card__name strong,
.id-card__details strong {
  color: var(--color-text-strong, #333);
}
</style>