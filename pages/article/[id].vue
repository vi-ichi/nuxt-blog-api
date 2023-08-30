<script setup lang="ts">
const { data } = await useFetch(
  `https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts/${useRoute().params.id}`
);
</script>

<template>
  <Header />
  <h1>{{ data.title }}</h1>
  <nuxt-img :src="data.image" placeholder />
  <div>{{ data.description }}</div>
</template>
