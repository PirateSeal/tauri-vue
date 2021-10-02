<template>
  <div>
    <MonacoEditor
        height="600"
        :code="code"
        :editorOptions="options"
        @mounted="onMounted"
        @codeChange="onCodeChange"
    >
    </MonacoEditor>
  </div>
</template>

<script>
import MonacoEditor from 'vue-monaco-editor'

export default {
  name: "Monaco",
  components: {
    MonacoEditor
  },
  props: {onFileToOpen: String},
  data() {
    return {
      code: '// Type away! \n',
      options: {
        selectOnLineNumbers: false
      }
    };
  },
  methods: {
    onMounted(editor) {
      this.editor = editor; //this.editor.setValue(new string)
    },
    fileToOpen(path){
      console.log(path)
      this.editor.setValue(path);
    },
    onCodeChange(editor) {
      console.log(editor.getValue());
    }
  }
}
</script>

<style scoped>

</style>
