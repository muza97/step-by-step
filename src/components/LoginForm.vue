<template>
  <div class="login-container">
    <h1>Step by Step - <span :class="{ 'fade-out': fadingOut }">{{ dynamicText }}</span></h1>
    <form @submit.prevent="login">
      <input type="text" v-model="username" placeholder="Username">
      <input type="password" v-model="password" placeholder="Password">
      <button type="submit">LOGIN</button>
    </form>
    <div class="social-media">
      <button>Sign up using Facebook</button>
      <button>Sign up using Google</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      password: '',
      dynamicText: 'learn to speak like a native',
      fadingOut: false
    };
  },
  mounted() {
    setTimeout(() => {
      this.fadeText();
    }, 3000);
  },
  methods: {
    login() {
      console.log(`Login attempted with username: ${this.username} and password: ${this.password}`);

      // Here you can insert any logic to validate the username and password.
      // For example, checking against hardcoded values or making an API call.

      // If the credentials are valid, redirect to the home page.
      // Adjust this condition as needed based on your actual validation logic.
      if (this.username && this.password) {
        this.$router.push('/home');
      } else {
        alert('Please enter both username and password.');
      }
    },
    fadeText() {
      this.fadingOut = true;
      setTimeout(() => {
        this.dynamicText = "AI your new tutor";
        this.fadingOut = false;
      }, 1000); 
    }
  }
}
</script>


<style scoped>
.login-container {
  max-width: 300px;
  margin: 100px auto;
  padding: 20px;
  background: white;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  text-align: center;
}
input, button {
  width: 100%;
  padding: 10px;
  margin: 10px 0;
  border-radius: 20px;
  border: none;
}
button {
  background-color: #8e44ad;
  color: white;
  cursor: pointer;
}
.social-media button {
  background: none;
  color: #3b5998; 
  margin-top: 5px;
}
span {
  display: inline-block;
  transition: opacity 0.5s ease-in-out;
  opacity: 1;
}
.fade-out {
  opacity: 0;
}
</style>
