<script>
export default {
  async asyncData({ params, $http }) {
    const articles = await $http.$get(
      `https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts`
    );

    return { articles };
  },
};
</script>

<template>
  <div>Главная страница</div>
</template>
