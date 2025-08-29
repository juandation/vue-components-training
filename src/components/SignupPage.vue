<template>
  <div class="signup-page">
    <h2>Sign Up</h2>
    
    <form class="signup-form">
      <div class="form-group">
        <label for="email">Email:</label>
        <input 
          id="email"
          type="email" 
          v-model="email"
          :class="{ valid: isEmailValid, invalid: email && !isEmailValid }"
          placeholder="Enter your email"
        />
      </div>
      
      <div class="form-group">
        <label for="password">Password:</label>
        <input 
          id="password"
          type="password" 
          v-model="password"
          :class="{ valid: isPasswordStrong, invalid: password && !isPasswordStrong }"
          placeholder="Enter your password"
        />
      </div>
      
      <div class="form-group">
        <label for="nationality">Nationality:</label>
        <select id="nationality" v-model="nationality">
          <option value="en">English</option>
          <option value="de">German</option>
          <option value="fr">French</option>
        </select>
      </div>
      
      <div class="greeting">
        {{ greeting }}
      </div>
      
      <div class="email-display">
        Your email is {{ email || 'john@doe.com' }}
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'SignupPage',
  data() {
    return {
      email: '',
      password: '',
      nationality: 'en'
    }
  },
  computed: {
    isEmailValid() {
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return emailRegex.test(this.email);
    },
    isPasswordStrong() {
      return this.password.length >= 8 && 
             /[A-Z]/.test(this.password) && 
             /[a-z]/.test(this.password) && 
             /[0-9]/.test(this.password);
    },
    greeting() {
      const greetings = {
        en: 'Hello',
        de: 'Hallo',
        fr: 'Bonjour'
      };
      return greetings[this.nationality];
    }
  }
}
</script>

<style scoped>
.signup-page {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  background: white;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.signup-form {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 5px;
}

label {
  font-weight: bold;
  color: #000;
}

input, select {
  padding: 10px;
  border: 2px solid #ddd;
  border-radius: 5px;
  font-size: 16px;
  transition: border-color 0.3s ease;
}

input:focus, select:focus {
  outline: none;
  border-color: #007bff;
}

input.valid {
  border-color: #28a745;
  background-color: #f8fff9;
}

input.invalid {
  border-color: #dc3545;
  background-color: #fff8f8;
}

.greeting {
  font-size: 24px;
  font-weight: bold;
  color: #007bff;
  text-align: center;
  padding: 15px;
  background: #ffffff;
  border: 2px solid #007bff;
  border-radius: 5px;
}

.email-display {
  font-size: 16px;
  color: #000;
  text-align: center;
  padding: 10px;
  background: #ffffff;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>