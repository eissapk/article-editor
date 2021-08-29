<template>
  <div class="editor">
    <!-- hint -->
    <section class="hint">
      <h3>Customization</h3>
      <p>The text will reflect mobile view</p>
    </section>

    <!-- title -->
    <div class="articleTitle">
      <input @input="getTitle" type="text" value="Text" placeholder="Article Title..." />
      <span v-html="icons.upArrow"></span>
    </div>

    <!-- editor -->
    <div id="editor_placeholder"></div>

    <!-- publish button -->
    <button type="button" id="publishBtn" v-html="icons.nextArrow"></button>
  </div>
</template>

<script>
  import suneditor from "suneditor";
  import plugins from "suneditor/src/plugins";
  export default {
    name: "Editor",
    data() {
      return {
        buttonList: [
          [
            "undo",
            "redo",
            "font",
            "fontSize",
            "formatBlock",
            "paragraphStyle",
            "blockquote",
            "bold",
            "underline",
            "italic",
            "strike",
            "subscript",
            "superscript",
            "fontColor",
            "hiliteColor",
            "textStyle",
            "removeFormat",
            "outdent",
            "indent",
            "align",
            "horizontalRule",
            "list",
            "lineHeight",
            "table",
            "link",
            "image",
            "showBlocks",
            "codeView",
          ],
        ],
        obj: {
          title: "Text",
          contents:
            "It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout.",
        },
        icons: {
          nextArrow: `
          Publish
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
          </svg>
          `,
          upArrow: `
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 15l7-7 7 7" />
          </svg>
          `,
        },
      };
    },
    mounted() {
      this.init();
    },
    methods: {
      init() {
        const editor = suneditor.create("editor_placeholder");
        editor.setOptions({ plugins: plugins, buttonList: this.buttonList, resizingBar: false });
        editor.setDefaultStyle("font-family: cursive; font-size: 16px; color:#000;");
        editor.setContents(this.obj.contents);
        editor.onChange = (contents, core) => {
          this.obj.contents = contents;
          this.sendData(this.obj);
        };
      },
      getTitle(e) {
        this.obj.title = e.target.value;
        this.sendData(this.obj);
      },
      sendData(obj) {
        this.$emit("editor-change", obj);
      },
    },
  };
</script>

<style lang="scss">
  .editor {
    margin: 50px 0;
    .hint {
      p {
        margin: 20px 0 30px;
      }
    }

    .articleTitle {
      position: relative;
      input {
        width: 100%;
        height: 40px;
        background: #efefef;
        border: none;
        text-indent: 35px;
        color: #000;
        font-weight: bold;
        margin-bottom: 20px;
        padding-right: 40px;
      }
      span {
        position: absolute;
        width: 25px;
        top: 7.5px;
        right: 10px;
        svg {
          width: 100%;
        }
      }
    }

    .sun-editor {
      width: 100% !important;
    }

    #publishBtn {
      background: #418dcb;
      color: white;
      border-radius: 3px;
      border: none;
      margin-top: 30px;
      padding: 0 10px;
      font-weight: bold;
      height: 40px;
      line-height: 40px;
      cursor: pointer;
      svg {
        width: 25px;
        top: 7px;
        position: relative;
        margin-left: 15px;
      }
    }
  }
</style>
