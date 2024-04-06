<template>
  <textarea class="textarea" v-model="value" placeholder="Type here..."></textarea>
</template>

<script lang="ts">
export default {
  data: () => ({
    value: '' || localStorage.getItem('source')
  }),
  watch: {
    value: {
      handler(value) {
        this.$emit('input', value)
      },
      immediate: true
    }
  },
  emits: ['input']
}
</script>

<style>
.textarea {
  width: 100%;
  resize: none;
  background: #151619;
  color: #fff;
  font-weight: 300;
  margin: 0 auto;
  overflow-y: auto;
  line-height: 1.45;
  min-height: 0;
  height: calc(100vh - 70px);
  padding: 1rem;
  outline: none;
  border: none;
  border-right: 0.25px #ffffff6d solid;
}
</style>
