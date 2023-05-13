<template>
  <div class="subscription-container">
    <form @submit.prevent="subscribe">
      <div>
        <label>Email:</label>
        <input v-model="email" type="email" placeholder="Email">
      </div>
      <div>
        <label>Username:</label>
        <input v-model="username" type="text" placeholder="Username">
      </div>
      <div>
        <label>Password:</label>
        <input v-model="password" type="password" placeholder="Password">
      </div>
      <div>
        <label>Accept Terms and Conditions:</label>
        <input v-model="termsAccepted" type="checkbox">
      </div>
      <button type="submit" :disabled="!isValid()">Subscribe</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      username: '',
      password: '',
      termsAccepted: false
    };
  },
  methods: {
    subscribe() {
      // Handle form submission
    },
    isValid() {
      // Implement your validation logic and return a boolean value
      return (
        this.email !== '' &&
        this.username !== '' &&
        this.password !== '' &&
        this.termsAccepted
      );
    }
  }
};
</script>

<style scoped>
.subscription-container {
  margin-top: 20px;
}

label {
  display: block;
  margin-bottom: 5px;
}

input {
  width: 200px;
  padding: 5px;
  margin-bottom: 10px;
}

button {
  padding: 10px 20px;
}
</style>