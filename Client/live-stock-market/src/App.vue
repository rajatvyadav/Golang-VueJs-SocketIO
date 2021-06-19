<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <button class="btn btn-primary" @click="traderLogin">Trader Login</button>
    <login v-if="!show"></login>
    <trader-login v-if="show" />
  </div>
</template>

<script>
import Login from './components/Login.vue'
import TraderLogin from './components/TraderLogin.vue'

export default {
  name: 'App',
  components: {
    Login,
    TraderLogin
  },
  data() {
      return {
        show: false
      }
    },
  methods: {
    traderLogin() {
      this.show = true
    }
  }
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
</style>
