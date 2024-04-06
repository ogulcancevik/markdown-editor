<template>
  <div class="header">
    <div class="title">
      <Document class="icon" />
      <div class="text">
        <span>Markdown Editor</span>
        <span>{{ fileName }}.md</span>
      </div>
    </div>
    <button @click="toggleMd" class="btn-show">
      {{ isShowMd ? 'Editor' : 'Preview' }}
    </button>
  </div>
</template>

<script>
import Document from './icons/Document.vue'
export default {
  components: { Document },
  data: () => ({
    fileName: 'Untitled',
    isShowMd: true
  }),
  methods: {
    toggleMd() {
      this.$emit('show', (this.isShowMd = !this.isShowMd))
    }
  },
  emits: ['show']
}
</script>

<style>
.header {
  background-color: #2c2d30;
  color: #fff;
  display: flex;
  padding-right: 1rem;
  padding-left: 1rem;
  height: 70px;
  width: 100%;
  align-items: center;
}
.title {
  display: flex;
  align-items: center;
  gap: 10px;
}
.text {
  display: flex;
  flex-direction: column;
  gap: 2.5px;
}
.text > span:nth-child(2) {
  font-size: 12px;
  color: #ccc;
}
.icon {
  width: 24px;
  height: 24px;
}
.btn-show {
  background-color: #4a4b4f;
  color: #fff;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.15s;
  display: none;
  position: absolute;
  right: 1rem;
}
.btn-show:hover {
  background-color: #3a3b3f;
}
@media (max-width: 768px) {
  .btn-show {
    display: block;
  }
}
</style>
