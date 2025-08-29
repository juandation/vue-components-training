<template>
  <div class="single-color-picker">
    <label :for="color" class="color-label">{{ color.toUpperCase() }}:</label>
    <input 
      :id="color"
      type="number" 
      :value="value"
      @input="handleChange"
      min="0" 
      max="255"
      class="color-input"
    />
    <div 
      class="color-preview" 
      :style="{ backgroundColor: previewColor }"
    ></div>
  </div>
</template>

<script>
export default {
  name: 'SingleColorPicker',
  props: {
    color: {
      type: String,
      required: true,
      validator: value => ['r', 'g', 'b'].includes(value)
    },
    value: {
      type: Number,
      required: true,
      validator: value => value >= 0 && value <= 255
    }
  },
  emits: ['change'],
  computed: {
    previewColor() {
      const colors = { r: 0, g: 0, b: 0 };
      colors[this.color] = this.value;
      return `rgb(${colors.r}, ${colors.g}, ${colors.b})`;
    }
  },
  methods: {
    handleChange(event) {
      const newValue = parseInt(event.target.value) || 0;
      const clampedValue = Math.max(0, Math.min(255, newValue));
      this.$emit('change', clampedValue);
    }
  }
}
</script>

<style scoped>
.single-color-picker {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 10px;
}

.color-label {
  font-weight: bold;
  min-width: 20px;
  color: #000;
}

.color-input {
  width: 80px;
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 3px;
  font-size: 14px;
}

.color-preview {
  width: 30px;
  height: 30px;
  border: 1px solid #ccc;
  border-radius: 3px;
}
</style>