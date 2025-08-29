<template>
  <div class="rgb-color-picker">
    <h3>RGB Color Picker</h3>

    <div class="color-controls">
      <SingleColorPicker
        color="r"
        :value="rValue"
        @change="updateColor('r', $event)"
      />
      <SingleColorPicker
        color="g"
        :value="gValue"
        @change="updateColor('g', $event)"
      />
      <SingleColorPicker
        color="b"
        :value="bValue"
        @change="updateColor('b', $event)"
      />
    </div>

    <div class="color-display">
      <div
        class="color-square"
        :style="{ backgroundColor: `rgb(${rValue}, ${gValue}, ${bValue})` }"
      ></div>
      <div class="color-values">
        <p>RGB({{ rValue }}, {{ gValue }}, {{ bValue }})</p>
        <p>{{ hexColor }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import SingleColorPicker from "./SingleColorPicker.vue";

export default {
  name: "RGBColorPicker",
  components: {
    SingleColorPicker,
  },
  data() {
    return {
      rValue: 255,
      gValue: 0,
      bValue: 0,
    };
  },
  computed: {
    hexColor() {
      const toHex = (value) =>
        value.toString(16).padStart(2, "0").toUpperCase();
      return `#${toHex(this.rValue)}${toHex(this.gValue)}${toHex(this.bValue)}`;
    },
  },
  methods: {
    updateColor(color, value) {
      if (color === "r") {
        this.rValue = value;
      } else if (color === "g") {
        this.gValue = value;
      } else if (color === "b") {
        this.bValue = value;
      }
    },
  },
};
</script>

<style scoped>
.rgb-color-picker {
  max-width: 400px;
  padding: 20px;
  background: white;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  margin: 0 auto;
}

.color-controls {
  margin-bottom: 20px;
}

.color-display {
  display: flex;
  align-items: center;
  gap: 20px;
}

.color-square {
  width: 150px;
  height: 150px;
  border: 2px solid #333;
  border-radius: 10px;
}

.color-values {
  flex: 1;
}

.color-values p {
  margin: 5px 0;
  font-family: monospace;
  font-size: 16px;
  font-weight: bold;
  color: #000;
}

h3 {
  margin-top: 0;
  color: #000;
  text-align: center;
}
</style>
