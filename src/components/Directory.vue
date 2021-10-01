<template>
  <div>
    <h1>Directory component</h1>
  </div>
</template>

<script>

import {read_dir} from "@tauri-apps/api"
import {onMounted} from "vue";

export default {
  name: "Directory",
  setup() {
    onMounted(async () => {
      console.log('mounted!');
      this.dirList = await read_dir("", {dir: 11})
    })
  },
  data() {
    return {
      dirList: []
    }
  }
}
</script>

<style scoped>

</style>
