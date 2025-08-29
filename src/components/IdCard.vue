<template>
  <div class="id-card">
    <div class="id-card__image">
      <img
        :src="picture"
        :alt="`${firstName} ${lastName}`"
        @error="handleImageError"
      />
    </div>
    <div class="id-card__info">
      <div class="id-card__name">
        <div><strong>First name:</strong> {{ firstName }}</div>
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
import { computed } from "vue";

const props = defineProps({
  lastName: {
    type: String,
    required: true,
  },
  firstName: {
    type: String,
    required: true,
  },
  gender: {
    type: String,
    required: true,
    validator: (value) => ["male", "female"].includes(value),
  },
  height: {
    type: Number,
    required: true,
  },
  birth: {
    type: Date,
    required: true,
  },
  picture: {
    type: String,
    required: true,
  },
});

const formattedBirthDate = computed(() => {
  return props.birth.toDateString();
});

const handleImageError = (event) => {
  console.warn("Failed to load profile image:", props.picture);
  // Set a fallback placeholder image when the original image fails to load
  event.target.src = "data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTUwIiBoZWlnaHQ9IjIwMCIgdmlld0JveD0iMCAwIDE1MCAyMDAiIGZpbGw9Im5vbmUiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+CjxyZWN0IHdpZHRoPSIxNTAiIGhlaWdodD0iMjAwIiBmaWxsPSIjRjNGNEY2Ii8+CjxjaXJjbGUgY3g9Ijc1IiBjeT0iNjAiIHI9IjI1IiBmaWxsPSIjOUNBM0FGIi8+CjxwYXRoIGQ9Ik0zMCAxNjBDMzAgMTM1IDUwIDExNSA3NSAxMTVTMTIwIDEzNSAxMjAgMTYwVjE4MEgzMFYxNjBaIiBmaWxsPSIjOUNBM0FGIi8+Cjwvc3ZnPgo=";
  // Remove the error event listener to prevent infinite loops
  event.target.onerror = null;
};
</script>

<style scoped>
.id-card {
  display: flex;
  border: 2px solid var(--color-border);
  border-radius: 8px;
  padding: 20px;
  margin: 10px 0;
  background: var(--color-background);
  max-width: 500px;
  font-family: Inter, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    Oxygen, Ubuntu, Cantarell, "Fira Sans", "Droid Sans", "Helvetica Neue",
    sans-serif;
  color: var(--color-text);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  transition: box-shadow 0.3s ease;
}

.id-card:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.id-card__image {
  flex-shrink: 0;
  width: 150px;
  margin-right: 20px;
}

.id-card__image img {
  width: 100%;
  height: 200px;
  border-radius: 4px;
  object-fit: cover;
  border: 1px solid var(--color-border);
}

.id-card__info {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  min-height: 200px;
}

.id-card__name {
  margin-bottom: 20px;
  padding-bottom: 15px;
  border-bottom: 1px solid var(--color-border);
}

.id-card__name div {
  margin-bottom: 8px;
  font-size: 16px;
  line-height: 1.4;
}

.id-card__details {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.id-card__details div {
  font-size: 14px;
  line-height: 1.5;
}

.id-card__name strong,
.id-card__details strong {
  color: var(--color-heading);
  font-weight: 600;
  margin-right: 8px;
}

/* Responsive design for smaller screens */
@media (max-width: 480px) {
  .id-card {
    flex-direction: column;
    max-width: 100%;
    padding: 15px;
  }

  .id-card__image {
    width: 100%;
    margin-right: 0;
    margin-bottom: 15px;
    text-align: center;
  }

  .id-card__image img {
    width: 150px;
    height: 200px;
  }

  .id-card__info {
    min-height: auto;
  }
}
</style>
