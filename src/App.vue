<template>
  <div id="app">
    <center>
      <img src="./assets/logo.png" alt="" />
      <h1>Navigation Drawer</h1>
      <button @click="toggleDrawer()">Open drawer</button>
    </center>
    <Drawer ref="drawer">
      <ul>
        <li>Item</li>
        <li>Item</li>
        <li>Item</li>
        <li>Item</li>
      </ul>
    </Drawer>
  </div>
</template>

<script>
import Drawer from './components/Drawer.vue'

export default {
  name: 'App',
  components: {
    Drawer
  },
  methods: {
    toggleDrawer() {
      this.$refs.drawer.toggle()
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
