<template>
  <VCard color="orange lighten-4" class="mx-auto fill-height" max-width="300px">
    <VImg v-if="image" :src="image" height="200px" cover />
    <VCardTitle class="text-left article-card--title">
      <BaseTitle>{{ title }}</BaseTitle>
    </VCardTitle>
    <VCardText class="text-left article-card--text">
      {{ body }}
    </VCardText>
    <VCardActions class="actions">
      <VBtn color="teal" block variant="elevated" @click="router.push(`/posts/${id}`)">
        Read more
      </VBtn>
    </VCardActions>
  </VCard>
</template>

<script setup lang="ts">
import type { Article } from 'assets/interfaces/Article'
import { useRouter } from 'vue-router'
const router = useRouter()
const props = withDefaults(defineProps<Article>(), {
  id: 0,
  title: 'Title should go there',
  body: 'Description of the article',
  image: '',
  userId: 0
})
</script>

<style scoped lang="scss">
.article-card--title {
  text-wrap: wrap;
  overflow: hidden;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  line-clamp: 2;
  -webkit-box-orient: vertical;
  max-height: 4rem;
  min-height: 4rem;
}

.article-card--text {
  text-wrap: wrap;
  overflow: hidden;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  line-clamp: 3;
  -webkit-box-orient: vertical;
  margin-bottom: 16px;
}
</style>
