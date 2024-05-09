<template>
  <div class="home-container">
    <header>
      <h1>Take your first step on Learning</h1>
      <button @click="logout" class="logout-button">Logout</button>
    </header>
    <div class="welcome-user">
      Welcome "{{ username }}"
      <span class="settings-icons"> 🔍</span>
    </div>
    <div class="feature-animation">
      <transition-group name="feature-list" tag="div">
        <div v-for="(feature, index) in features" :key="feature" :class="{'feature-item': true, 'active': index === activeFeature}">
          {{ feature }}
        </div>
      </transition-group>
    </div>
      <div class="conversation-start">
        <button @click="startConversation"><i class="fas fa-microphone"></i> Press to start a conversation in Swedish</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      features: ['Easy to use', 'Press of a button', 'Totally Free'],
      activeFeature: 0
    };
  },
  mounted() {
    this.animateFeatures();
    this.username = localStorage.getItem('user'); 
  },
  methods: {
    animateFeatures() {
      setInterval(() => {
        this.activeFeature = (this.activeFeature + 1) % this.features.length;
      }, 3000); 
    },
    startConversation() {
      console.log('Starting conversation...');
      // Implement conversation logic or redirect
    },
    logout() {
      console.log('Logging out...');
      localStorage.removeItem('user'); // Clear user data
      this.$router.push('/'); 
    }
  }
}
</script>

<style scoped>
.home-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 10px 0;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
}

h1 {
  margin-left: 10px; 
}

.logout-button {
  margin-right: 10px;
}

.welcome-user {
  margin-top: 60px; 
}

.feature-animation {
  margin: 20px;
}

.feature-item {
  opacity: 0;
  transition: opacity 1s;
}

.feature-item.active {
  opacity: 1;
}

.conversation-start button {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 20px;
  font-size: 16px;
  border-radius: 20px;
  background-color: #4CAF50; 
  color: white;
  border: none;
  cursor: pointer;
}

.conversation-start button i, .conversation-start button svg {
  margin-right: 10px;
}
</style>
