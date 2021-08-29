<template>
  <div class="preview">
    <div id="img">
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
    margin-bottom: 50px;
    #img {
      position: relative;
      background-image: url("../assets/iphone.svg");
      background-repeat: no-repeat;
      background-size: 100% auto;
      background-position: center top;
      margin: 0 auto;
      height: 625px;
      width: 100%;
      max-width: 320px;

      article {
        position: absolute;
        top: 90px;
        left: 0;
        right: 0;
        margin: 0 auto;
        width: calc(100% * 0.8);
        padding: 10px;
        box-sizing: border-box;
        max-height: calc(450px - 20px);
        overflow: auto;
        border-radius: 25px;

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
        }
      }
    }
  }
</style>
