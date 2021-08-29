<template>
  <div class="preview">
    <div id="img">
      <img src="../assets/iphone.svg" alt="iphone" />
      <article>
        <h3 v-html="obj.title"></h3>
        <p class="se-wrapper-inner se-wrapper-wysiwyg sun-editor-editable" v-html="obj.contents"></p>
      </article>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Preview",
    props: ["obj"],
  };
</script>

<style lang="scss" scoped>
  .preview {
    position: relative;
    #img {
      display: inline-block;
      position: relative;
      transform: translateX(-50%);
      left: 50%;

      img {
        display: block;
        width: 100%;
      }

      article {
        position: absolute;
        top: 80px;
        left: 30px;
        overflow: auto;
        border-radius: 25px;
        width: calc(100% - 60px);
        height: calc(100% - 175px);
        box-sizing: border-box;
        background: #fff;
        padding: 10px;

        &::-webkit-scrollbar {
          width: 5px;
          border-radius: 25px;
        }

        &::-webkit-scrollbar-track {
          background: #eeeeee;
          border-radius: 25px;
        }

        &::-webkit-scrollbar-thumb {
          background-color: #d1d1d1;
          border-radius: 25px;
        }
        h3 {
          text-align: center;
          margin: 20px 0;
        }
        p {
          font-size: inherit;
          color: #000;
          padding: 0;
          margin: 0;
        }
      }
    }
  }
</style>
