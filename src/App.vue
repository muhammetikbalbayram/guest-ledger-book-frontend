<template>
  <div id="app">
    <guest-ledger></guest-ledger>
  </div>
</template>

<script>
import GuestLedger from './components/GuestLedger.vue'

export default {
  name: 'App',
  components: {
    GuestLedger
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

