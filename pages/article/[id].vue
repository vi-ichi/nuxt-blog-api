<script setup lang="ts">
const { data } = await useFetch(
  `https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts/${
    useRoute().params.id
  }`
);
</script>

<template>
  <h1 class="text-8xl mt-[158px] mb-[73px]">{{ data.title }}</h1>
  <div class="aspect-video">
    <img :src="data.image" class="w-full h-full object-cover" />
  </div>
  <div class="mt-20 mb-8">About</div>
  <div class="mb-20 max-w-2xl text-3xl">{{ data.description }}</div>
</template>
