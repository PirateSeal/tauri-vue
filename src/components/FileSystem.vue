<template>
  <div>
    <h1>FileSystem component</h1>
    <ul>
      <li v-for="item in dirList" :key="item" v-on:click="readDirectory(item)">
        <div>
          <h2>{{ item.name }}</h2>
        </div>
      </li>
    </ul>

  </div>
</template>

<script>

import {fs, path as tauri_path} from "@tauri-apps/api"


export default {
  name: "FileSystem",
  async mounted() {
    try {
      this.dirList = await fs.readDir("", {dir: 11})
    } catch (e) {
      console.error(e)
    }
  },
  props: {fileToOpen: String},
  emits: ["fileToOpen"],
  methods: {

    async readDirectory(item) {
      try {
        // j'ai essayé de faire ça mieux mais ça ne voulait plus fonctionner
        // du coup je suis resté à cette version pour que je puisse avoir
        // une nav fonctionnelle ¯\_(ツ)_/¯

        let parentPath = "";
        let parentPathTab = []
        parentPathTab = item.path.split(tauri_path.sep)
        parentPath = parentPathTab.splice(0, parentPathTab.length - 1).join(tauri_path.sep)

        let dirlist = await fs.readDir(item.path);
        let parent = {name: "..", path: parentPath};
        dirlist.splice(0, 0, parent)
        this.dirList = dirlist


        //events de ses morts qui ne veulent pas lire les fichiers dans monaco
        //this.$emit("fileToOpen", item.path)


      } catch (e) {
        console.error(e)
      }

    }
  }
  ,
  data() {
    return {
      dirList: []
    }
  }
}
</script>

<style scoped>

</style>
