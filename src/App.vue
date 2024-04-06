<template>
  <MainLayout>
    <template v-slot:header><Header @show="toggleMd" /></template>
    <template v-slot:editor><Editor v-show="isShowEditor" @input="updateSource" /></template>
    <template v-slot:preview><MarkdownPreview v-show="isShowMd" :source="source" /></template>
  </MainLayout>
</template>

<script lang="ts">
import MainLayout from './layouts/MainLayout.vue'
import Editor from './components/Editor.vue'
import Header from './components/Header.vue'
import MarkdownPreview from './components/MarkdownPreview.vue'
export default {
  components: {
    MainLayout,
    Editor,
    MarkdownPreview,
    Header
  },
  data: () => ({
    source: '',
    windowWidth: window.innerWidth as number,
    isShowMd: false as boolean,
    isShowEditor: true as boolean
  }),
  methods: {
    updateSource(value: string) {
      this.source = value as string
      localStorage.setItem('source', value)
    },
    handleResize() {
      this.windowWidth = window.innerWidth
    },
    toggleMd($event: boolean) {
      this.isShowMd = !$event
      this.isShowEditor = $event
    }
  },
  mounted() {
    window.addEventListener('resize', this.handleResize)
    this.source = localStorage.getItem('source') || ''
  },
  watch: {
    windowWidth: {
      handler() {
        this.isShowMd = this.windowWidth > 768
        if (this.windowWidth <= 768) this.isShowEditor = true
      },
      immediate: true
    }
  }
}
</script>
