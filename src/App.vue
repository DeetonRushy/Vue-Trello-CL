<template>
  <MellowBanner msg="Mellow"/>
  <HomeView />
</template>

<script>
import MellowBanner from './components/Banner.vue'
import HomeView from './components/HomeView'

export default {
  name: 'App',
  components: {
    MellowBanner,
    HomeView
  }
}
</script>

<style>

* {
  font-family: monospace;
}

html{
  background-color: white;
}

div[class="ticket-content-popup"] {
  position: absolute;
  margin: auto;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
