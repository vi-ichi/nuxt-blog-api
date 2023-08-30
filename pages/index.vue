<script setup lang="ts">
const { data } = await useFetch(
  `https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts`
);
</script>

<template>
  <div>Главная страница</div>
</template>
