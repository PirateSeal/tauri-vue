<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Directory/>
</template>

<script>
import Directory from './components/Directory'

export default {
  name: 'App',
  components: {
    Directory
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
