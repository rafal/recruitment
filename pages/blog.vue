<template>
  <VContainer class="text-center">
    <VRow>
      <VCol cols="12">
        <h1> Blog </h1>
      </VCol>

      <VCol
        v-for="article in articles"
        v-if="!loading"
        cols="3"
      >
        <ArticleCard :id="article.id" :title="article.title" :body="article.body" />
      </VCol>
      <VCol v-else cols="12" >
        <VProgressCircular indeterminate />
      </VCol>
    </VRow>
  </VContainer>
</template>

<script setup lang="ts">
import axios from 'axios';
import type { Article } from 'assets/interfaces/Article';
import ArticleCard from '~/components/Blog/ArticleCard.vue';

const articles = ref<Article[]>([]);
const loading = ref<boolean>(false);

onMounted(async () => {
  loading.value = true;
  // Docs: https://jsonplaceholder.typicode.com/
  const response = await axios.get('https://jsonplaceholder.typicode.com/posts');
  console.log('Response:', response);
  articles.value = response.data as Article[];
  loading.value = false;
});
</script>

<style scoped lang="scss">
.footer {
  background-color: #f5f5f5;
  padding: 16px;
  text-align: center;
  width: 100%;
}
</style>
