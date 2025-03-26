<template>
  <VContainer>
    <VRow>
      <VCol cols="12">
        <VBtn color="secondary" to="/blog" prepend-icon="mdi-arrow-left"> Back to Blog </VBtn>
      </VCol>

      <template v-if="!pending">
        <template v-if="post">
          <VCol cols="12">
            <h1>Post {{ id }}</h1>
          </VCol>

          <VCol cols="12">
            <BaseTitle>
              {{ post.title }}
            </BaseTitle>
          </VCol>

          <VCol cols="12">
            {{ post.body }}
          </VCol>
        </template>

        <VCol v-else cols="12">
          <VAlert type="error"> Post not found </VAlert>
        </VCol>
      </template>

      <VCol v-else cols="12" class="text-center">
        <VProgressCircular indeterminate />
      </VCol>
    </VRow>
  </VContainer>
</template>

<script setup lang="ts">
import type { Article } from '~/assets/interfaces/Article'

// Get the post ID from route params
const route = useRoute()
const id = ref(route.params.id)

// Fetch the post data
const {
  data: post,
  pending,
  error
} = useFetch<Article>(() => `https://jsonplaceholder.typicode.com/posts/${id.value}`)

// Handle errors
if (error.value) {
  console.error('Error fetching post:', error.value)
}
</script>

<style scoped lang="scss">
h1 {
  margin-bottom: 1rem;
}
</style>
