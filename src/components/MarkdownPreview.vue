<template>
  <div class="markdown" v-if="mdtoHtml" v-html="mdtoHtml"></div>
  <div class="placeholder" v-else>No content</div>
</template>
<script>
import { marked } from 'marked'
export default {
  name: 'MarkdownPreview',
  props: {
    source: {
      type: String,
      required: true
    }
  },
  computed: {
    mdtoHtml() {
      return marked(this.source, {
        gfm: true,
        breaks: true,
        sanitize: true
      })
    }
  }
}
</script>
<style>
.markdown {
  width: 100%;
  background: #151619;
  color: #fff;
  font-weight: 300;
  margin: 0 auto;
  line-height: 2.5;
  padding: 1.5rem;
  padding-left: 2rem;
  min-height: 0;
  overflow-y: auto;
  font-size: 0.9rem;
  height: calc(100vh - 70px);
  border-right: 0.25px #ffffff6d solid;
}
.placeholder {
  height: calc(100vh - 70px);
  padding: 1rem;
  background: #151619;
  color: #676767;
}
</style>
