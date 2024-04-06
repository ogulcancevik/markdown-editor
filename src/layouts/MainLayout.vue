<template>
  <div class="layout">
    <slot name="header" />
    <div class="markdown-container">
      <slot name="editor" />
      <slot name="preview" />
    </div>
  </div>
</template>

<style>
.layout {
  display: flex;
  flex-direction: column;
}
.markdown-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
}
@media (max-width: 768px) {
  .markdown-container {
    grid-template-columns: 1fr;
  }
}
</style>
