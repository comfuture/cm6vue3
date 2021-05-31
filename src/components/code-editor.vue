<template>
  <div ref="editor"></div>
</template>

<script>
import { onMounted, ref } from "vue";
import { EditorState, EditorView, basicSetup } from "@codemirror/basic-setup";
import { ViewPlugin } from '@codemirror/view';
import { javascript } from "@codemirror/lang-javascript";

export default {
  name: 'code-editor',
  props: {
    modelValue: {
      type: String,
      default: () => ''
    }
  },
  emits: ['update:modelValue'],
  setup(props, { emit }) {
    const editor = ref(null);
    onMounted(() => {
      const updateValue = (e, cm) => {
        const code = cm.state.doc.toString()
        emit('update:modelValue', code)
      }
      const events = ['blur', 'keyup', 'paste', 'cut', 'delete', 'mouseup']
      const eventHandler = ViewPlugin.define(cm => null, {
        eventHandlers: Object.fromEntries(events.map(e => [e, updateValue]))
      })
      const cm = new EditorView({
        state: EditorState.create({
          extensions: [basicSetup, javascript(), eventHandler],
          doc: props.modelValue,
        }),
        parent: editor.value
      });
    });
    return { editor };
  }
}
</script>
<style scoped>
.cm-editor {
  height: 100%;
  border: solid 1px #ddd;
  border-radius: 4px;
}
</style>