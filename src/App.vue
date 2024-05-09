<template>
  <div id="app">
    <router-view></router-view> <!-- This tag renders the current route component -->
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  background: linear-gradient(to right, #8e44ad, #3498db);
  color: #fff;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
}

</style>