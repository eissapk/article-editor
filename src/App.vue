<template>
  <div id="app">
    <Preview :obj="obj" />
    <Editor @editor-change="update" />
  </div>
</template>

<script>
  import Preview from "../src/components/Preview";
  import Editor from "../src/components/Editor";
  export default {
    name: "App",
    components: { Preview, Editor },
    data() {
      return {
        obj: {
          title: "Text",
          contents:
            "It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout.",
        },
      };
    },
    methods: {
      update(obj) {
        this.obj = obj;
      },
    },
  };
</script>

<style lang="scss">
  @import "../src/app.scss";
</style>
