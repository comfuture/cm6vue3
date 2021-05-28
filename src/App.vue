<template>
  <code-editor v-model="code"></code-editor>
</template>

<script>
import { ref } from 'vue'
import CodeEditor from './components/code-editor'

export default {
  name: 'App',
  components: {
    CodeEditor
  },
  setup(props) {
    let code = ref(`const answer = 42;`);
    return { code };
  }
}
</script>
<style scoped>
.cm-editor {
  height: 200px;
  border: solid 1px #ddd;
  border-radius: 4px;
}
</style>