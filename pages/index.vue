<script setup lang="ts">
const { data } = await useFetch(
  `https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts`
);

const active = ref(-1);
</script>

<template>
  <h1 class="text-7xl mb-[39px] mt-[158px]">Articles</h1>
  <div class="grid grid-cols-4 gap-8 mb-32">
    <div v-for="a in data.reverse().slice(0, 8)">
      <NuxtLink
        @mouseover="active = a.id"
        @mouseleave="active = -1"
        :to="'/article/' + a.id"
        class="text-lg"
      >
        <div class="aspect-square">
          <img :src="a.image" class="w-full h-full object-none" />
        </div>
        <div class="my-6">{{ a.preview }}</div>
        <div class="text-[#E2BEFF]">{{  active === a.id ? "Read more" : "&nbsp;" }}</div>
      </NuxtLink>
    </div>
  </div>
</template>
