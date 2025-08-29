<template>
  <img 
    :src="currentDiceImage" 
    alt="Dice" 
    class="dice"
    @click="rollDice"
  />
</template>

<script>
export default {
  name: 'Dice',
  data() {
    return {
      currentDice: Math.floor(Math.random() * 6) + 1,
      isRolling: false
    }
  },
  computed: {
    currentDiceImage() {
      if (this.isRolling) {
        return '/src/assets/images/dice-empty.png';
      }
      return `/src/assets/images/dice${this.currentDice}.png`;
    }
  },
  methods: {
    rollDice() {
      if (this.isRolling) return;
      
      this.isRolling = true;
      
      setTimeout(() => {
        this.currentDice = Math.floor(Math.random() * 6) + 1;
        this.isRolling = false;
      }, 1000);
    }
  }
}
</script>

<style scoped>
.dice {
  width: 100px;
  height: 100px;
  cursor: pointer;
  transition: transform 0.1s ease;
}

.dice:hover {
  transform: scale(1.1);
}

.dice:active {
  transform: scale(0.9);
}
</style>