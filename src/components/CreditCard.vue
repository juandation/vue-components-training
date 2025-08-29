<template>
  <div 
    class="credit-card" 
    :style="{ backgroundColor: bgColor, color: color }"
  >
    <div class="card-header">
      <div class="card-type">{{ type }}</div>
    </div>
    <div class="card-number">
      •••• •••• •••• {{ lastFourDigits }}
    </div>
    <div class="card-details">
      <div class="expiration">
        Expires {{ formattedMonth }}/{{ expirationYear }}
      </div>
      <div class="bank">{{ bank }}</div>
    </div>
    <div class="card-owner">{{ owner }}</div>
  </div>
</template>

<script>
export default {
  name: 'CreditCard',
  props: {
    type: {
      type: String,
      required: true,
      validator: value => ['Visa', 'Master Card'].includes(value)
    },
    number: {
      type: String,
      required: true
    },
    expirationMonth: {
      type: Number,
      required: true,
      validator: value => value >= 1 && value <= 12
    },
    expirationYear: {
      type: Number,
      required: true
    },
    bank: {
      type: String,
      required: true
    },
    owner: {
      type: String,
      required: true
    },
    bgColor: {
      type: String,
      required: true
    },
    color: {
      type: String,
      required: true
    }
  },
  computed: {
    lastFourDigits() {
      return this.number.slice(-4);
    },
    formattedMonth() {
      return this.expirationMonth.toString().padStart(2, '0');
    }
  }
}
</script>

<style scoped>
.credit-card {
  width: 350px;
  height: 200px;
  border-radius: 10px;
  padding: 15px;
  margin: 10px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  font-family: 'Courier New', monospace;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  box-sizing: border-box;
}

.card-header {
  display: flex;
  justify-content: flex-end;
  margin-bottom: 10px;
}

.card-type {
  font-size: 16px;
  font-weight: bold;
}

.card-number {
  font-size: 20px;
  font-weight: bold;
  letter-spacing: 2px;
  margin: 15px 0;
  flex-grow: 1;
  display: flex;
  align-items: center;
}

.card-details {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 12px;
  margin-bottom: 10px;
}

.card-owner {
  font-size: 14px;
  font-weight: bold;
  text-transform: uppercase;
}
</style>