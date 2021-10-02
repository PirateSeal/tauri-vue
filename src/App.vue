<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <FileSystem @fileToOpen="updateFileToOpen"/>
  <Monaco @fileToOpen="path"/>
</template>

<script>
import FileSystem from './components/FileSystem'
import Monaco from "@/components/Monaco";

export default {
  name: 'App',
  components: {
    Monaco,
    FileSystem
  },
  emits: ["path"],
  methods: {
    updateFileToOpen(path) {
      this.$emit('fileToOpen', path)
    }
  },
  data() {
    return {
      path: ""
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
