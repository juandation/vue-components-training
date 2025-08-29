<template>
  <div 
    class="box-color" 
    :style="{ 
      backgroundColor: `rgb(${r}, ${g}, ${b})`,
      color: textColor
    }"
  >
    rgb({{ r }}, {{ g }}, {{ b }})
  </div>
</template>

<script>
export default {
  name: 'BoxColor',
  props: {
    r: {
      type: Number,
      required: true,
      validator: value => value >= 0 && value <= 255
    },
    g: {
      type: Number,
      required: true,
      validator: value => value >= 0 && value <= 255
    },
    b: {
      type: Number,
      required: true,
      validator: value => value >= 0 && value <= 255
    }
  },
  computed: {
    textColor() {
     
      const luminance = (0.299 * this.r + 0.587 * this.g + 0.114 * this.b) / 255;
      return luminance > 0.5 ? '#000000' : '#ffffff';
    }
  }
}
</script>

<style scoped>
.box-color {
  width: 200px;
  height: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: monospace;
  font-size: 14px;
  font-weight: bold;
  border: 1px solid #ccc;
  margin: 10px 0;
}
</style>