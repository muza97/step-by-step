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
    
    <div class="header">
      <div>
        <svg class="waves" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
        viewBox="0 24 150 28" preserveAspectRatio="none" shape-rendering="auto">
          <defs>
            <path id="gentle-wave" d="M-160 44c30 0 58-18 88-18s 58 18 88 18 58-18 88-18 58 18 88 18 v44h-352z" />
          </defs>
          <g class="parallax">
            <use xlink:href="#gentle-wave" x="48" y="0" fill="rgba(255,255,255,0.7)" />
            <use xlink:href="#gentle-wave" x="48" y="3" fill="rgba(255,255,255,0.5)" />
            <use xlink:href="#gentle-wave" x="48" y="5" fill="rgba(255,255,255,0.3)" />
            <use xlink:href="#gentle-wave" x="48" y="7" fill="#fff" />
          </g>
        </svg>
      </div>
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
      
    },
    logout() {
      console.log('Logging out...');
      localStorage.removeItem('user'); 
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
  min-height: 100vh; 
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

.header {
  position: relative; 
  text-align: center;
  /* background: linear-gradient(60deg, rgba(84,58,183,1) 0%, rgba(0,172,193,1) 100%); */
  color: white;
  width: 100%; 
  margin-top: auto; 
}

.waves {
  position: relative;
  width: 100%;
  height: 15vh;
  margin-bottom: -7px; 
  min-height: 100px;
  max-height: 150px;
}

.parallax > use {
  animation: move-forever 25s cubic-bezier(.55,.5,.45,.5) infinite;
}

.parallax > use:nth-child(1) { animation-delay: -2s; animation-duration: 7s; }
.parallax > use:nth-child(2) { animation-delay: -3s; animation-duration: 10s; }
.parallax > use:nth-child(3) { animation-delay: -4s; animation-duration: 13s; }
.parallax > use:nth-child(4) { animation-delay: -5s; animation-duration: 20s; }

@keyframes move-forever {
  0% { transform: translate3d(-90px,0,0); }
  100% { transform: translate3d(85px,0,0); }
}
</style>
