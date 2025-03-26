<template>
  <VContainer class="text-center">
    <VRow>
      <VCol cols="12">
        <h1>Blog</h1>
      </VCol>
      <template v-if="!loading">
        <VCol v-for="article in articles" cols="3" :key="article.id">
          <BlogArticleCard
            :id="article.id"
            :title="article.title"
            :body="article.body"
            :userId="article.userId"
            :image="article.image"
          />
        </VCol>
      </template>
      <VCol v-else cols="12">
        <VProgressCircular indeterminate />
      </VCol>
    </VRow>
  </VContainer>
</template>

<script setup lang="ts">
import type { Article } from '~/assets/interfaces/Article'

// Docs: https://jsonplaceholder.typicode.com/
const { data: articles, pending: loading } = await useFetch<Article[]>(
  'https://jsonplaceholder.typicode.com/posts'
)
</script>

<style scoped lang="scss"></style>
