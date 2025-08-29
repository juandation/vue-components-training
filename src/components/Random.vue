<template>
  <div class="random">
    {{ randomNumber }}
  </div>
</template>

<script>
export default {
  name: 'Random',
  props: {
    min: {
      type: Number,
      required: true
    },
    max: {
      type: Number,
      required: true
    }
  },
  computed: {
    randomNumber() {
      return Math.floor(Math.random() * (this.max - this.min + 1)) + this.min;
    }
  }
}
</script>

<style scoped>
.random {
  font-size: 1.2em;
  font-weight: bold;
  padding: 0.5em;
  background-color: white;
  color: black;
  border: 2px solid #333;
  border-radius: 5px;
  display: inline-block;
  margin: 5px;
  min-width: 50px;
  text-align: center;
}
</style>