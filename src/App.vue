<template>
  <code-editor v-model="code" class="edit-area"></code-editor>
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
.edit-area {
  height: 300px;
}
</style>