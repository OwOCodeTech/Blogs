<script setup>
import DefaultTheme from 'vitepress/theme'
import { useData } from 'vitepress'
import { computed } from 'vue'
import Comments from './components/Comments.vue'
import ImagePreview from './components/ImagePreview.vue'

const { Layout } = DefaultTheme
const { frontmatter } = useData()
</script>

<template>
  <Layout>
    <template #doc-after>
      <Comments v-if="!frontmatter.home" />
      <ImagePreview />
    </template>
  </Layout>
</template>

<style>
/* 确保内容区域不会溢出 */
:deep(.VPDoc) {
  max-width: var(--vp-layout-max-width);
  margin: 0 auto;
}

:deep(.VPDoc .container) {
  max-width: calc(var(--vp-layout-max-width) - var(--vp-sidebar-width) - var(--vp-aside-width));
  margin: 0 auto;
  padding: 0 24px;
  box-sizing: border-box;
}

@media (max-width: 960px) {
  :deep(.VPDoc .container) {
    max-width: 100%;
    padding: 0 16px;
  }
}
</style> 