<template>
  <div class="facebook">
    <div class="country-filters">
      <button 
        v-for="country in countries" 
        :key="country"
        @click="selectCountry(country)"
        :class="{ active: selectedCountry === country }"
        class="country-btn"
      >
        {{ country }}
      </button>
      <button 
        @click="clearFilter"
        :class="{ active: selectedCountry === null }"
        class="country-btn"
      >
        All
      </button>
    </div>
    
    <div class="profiles-grid">
      <div 
        v-for="profile in profiles" 
        :key="`${profile.firstName}-${profile.lastName}`"
        class="profile-card"
        :class="{ highlighted: selectedCountry === profile.country }"
        @click="toggleProfileDetails(profile)"
      >
        <img :src="profile.img" :alt="`${profile.firstName} ${profile.lastName}`" class="profile-image" />
        
        <div v-if="expandedProfile === profile" class="profile-details">
          <h3>{{ profile.firstName }} {{ profile.lastName }}</h3>
          <p><strong>Country:</strong> {{ profile.country }}</p>
          <p><strong>Status:</strong> {{ profile.isStudent ? 'Student' : 'Not Student' }}</p>
        </div>
        
        <div v-else class="profile-name">
          {{ profile.firstName }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import profiles from '../assets/data/berlin.json'

export default {
  name: 'FaceBook',
  data() {
    return {
      profiles,
      selectedCountry: null,
      expandedProfile: null
    }
  },
  computed: {
    countries() {
      const uniqueCountries = [...new Set(this.profiles.map(profile => profile.country))];
      return uniqueCountries.sort();
    }
  },
  methods: {
    selectCountry(country) {
      this.selectedCountry = country;
    },
    clearFilter() {
      this.selectedCountry = null;
    },
    toggleProfileDetails(profile) {
      this.expandedProfile = this.expandedProfile === profile ? null : profile;
    }
  }
}
</script>

<style scoped>
.facebook {
  padding: 20px;
  background: white;
  border-radius: 8px;
}

.country-filters {
  margin-bottom: 20px;
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.country-btn {
  padding: 8px 16px;
  border: 1px solid #ccc;
  background: white;
  border-radius: 5px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.country-btn:hover {
  background: #f0f0f0;
}

.country-btn.active {
  background: #007bff;
  color: white;
  border-color: #007bff;
}

.profiles-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 20px;
}

.profile-card {
  border: 1px solid #ddd;
  border-radius: 10px;
  padding: 15px;
  text-align: center;
  cursor: pointer;
  transition: all 0.3s ease;
  background: white;
}

.profile-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}

.profile-card.highlighted {
  background: #e3f2fd;
  border-color: #2196f3;
}

.profile-image {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  object-fit: cover;
  margin-bottom: 10px;
}

.profile-name {
  font-weight: bold;
  font-size: 16px;
  color: #222;
}

.profile-details h3 {
  margin: 10px 0 5px 0;
  color: #333;
}

.profile-details p {
  margin: 5px 0;
  font-size: 14px;
  color: #222;
}
</style>