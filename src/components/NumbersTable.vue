<template>
  <div class="numbers-table">
    <div 
      v-for="number in numbers" 
      :key="number"
      class="number-cell"
      :class="{ even: number % 2 === 0 }"
    >
      {{ number }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'NumbersTable',
  props: {
    limit: {
      type: Number,
      required: true,
      validator: value => value > 0
    }
  },
  computed: {
    numbers() {
      const nums = [];
      for (let i = 1; i <= this.limit; i++) {
        nums.push(i);
      }
      return nums;
    }
  }
}
</script>

<style scoped>
.numbers-table {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(50px, 1fr));
  gap: 5px;
  padding: 20px;
  max-width: 400px;
}

.number-cell {
  width: 50px;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid #ccc;
  font-size: 18px;
  font-weight: bold;
  background-color: white;
  color: black;
}

.number-cell.even {
  background-color: red;
  color: white;
}
</style>