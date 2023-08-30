<script>
export default {
  async asyncData({ params, $http }) {
    const article = await $http.$get(
      `https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts/${params.id}`
    );

    return { article };
  },
};
</script>

<template>
  <div>Страница статьи</div>
</template>
