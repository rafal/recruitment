<template>
  <VContainer>
    <VRow>
      <VCol cols="12">
        <h1>Post {{ id }}</h1>
      </VCol>

      <VCol cols="12">
        <BaseTitle>
          Post title
        </BaseTitle>
      </VCol>

      <VCol cols="12">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Expedita iure odit quae quia repellat repellendus, sapiente soluta ut vitae voluptatem. A ab adipisci, aliquam architecto asperiores atque consectetur consequatur corporis deleniti incidunt ipsum odit optio, quo quod rem similique tempora, veritatis voluptatibus! Dolore nisi nostrum quam, rem vero voluptates voluptatum.
      </VCol>
    </VRow>
  </VContainer>
</template>

<script setup>
const rotue = useRoute();
const id = ref(rotue.params.id);
</script>

<style scoped lang="scss">

</style>
