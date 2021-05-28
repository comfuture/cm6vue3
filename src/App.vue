<template>
  <code-editor v-model="code"></code-editor>
</template>

<script>
import CodeEditor from './components/code-editor';

export default {
  name: 'App',
  components: {
    CodeEditor
  },
  setup(props) {
    let code = `const answer = 42;`;
    const printChanges = v => {
      alert(v);
    }
    return { code, printChanges };
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