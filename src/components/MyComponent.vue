<template>
  <codemirror
    v-model="code"
    placeholder="There is no code..."
    :style="{ height: '600px' }"
    :autofocus="true"
    :indent-with-tab="true"
    :tab-size="2"
    :extensions="extensions"
    @ready="handleReady"
  />
</template>

<script>
import { defineComponent } from "vue";
import { Codemirror } from "vue-codemirror";
import { oneDark } from "@codemirror/theme-one-dark";
import { xml } from "@codemirror/lang-xml";
import { ref, shallowRef } from "vue";
import beautify from "xml-beautifier";

export default defineComponent({
  components: {
    Codemirror,
  },
  setup() {
    const formattedXml =
      '<?xml version="1.0" encoding="ISO-8859-1"?><note><to>Tove</to><from>Jani</from><heading>Reminder</heading><body>Don\'t forget me this weekend!</body></note>';
    const code = ref(beautify(formattedXml));

    const extensions = [xml(), oneDark];

    // Codemirror EditorView instance ref
    const view = shallowRef();
    const handleReady = (payload) => {
      view.value = payload.view;
    };

    return {
      code,
      extensions,
      handleReady,
    };
  },
});
</script>

<style scoped></style>
