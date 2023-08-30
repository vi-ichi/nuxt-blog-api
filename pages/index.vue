<script setup lang="ts">
const { data } = await useFetch(
  `https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts`
);

const active = ref(-1);
</script>

<template>
  <h1 class="text-7xl mb-[39px] mt-[158px]">Articles</h1>
  <div class="grid grid-cols-4 gap-8 mb-10">
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
        <div class="text-[#E2BEFF]">
          {{ active === a.id ? "Read more" : "&nbsp;" }}
        </div>
      </NuxtLink>
    </div>
  </div>
  <div class="flex mb-32 gap-2 text-md">
    <NuxtLink
      to="/?page=1"
      class="w-[44px] h-[44px] justify-center flex items-center rounded-xl"
      :class="{
        'bg-black text-white':
          $route.query.page !== '2' &&
          $route.query.page !== '3' &&
          $route.query.page !== '4' &&
          $route.query.page !== '5',
      }"
    >
      1
    </NuxtLink>
    <NuxtLink
      to="/?page=2"
      class="w-[44px] h-[44px] justify-center flex items-center rounded-xl"
      :class="{ 'bg-black text-white': $route.query.page === '2' }"
    >
      2
    </NuxtLink>
    <NuxtLink
      to="/?page=3"
      class="w-[44px] h-[44px] justify-center flex items-center rounded-xl"
      :class="{ 'bg-black text-white': $route.query.page === '3' }"
    >
      3
    </NuxtLink>
    <NuxtLink
      to="/?page=4"
      class="w-[44px] h-[44px] justify-center flex items-center rounded-xl"
      :class="{ 'bg-black text-white': $route.query.page === '4' }"
    >
      4
    </NuxtLink>
    <NuxtLink
      to="/?page=5"
      class="w-[44px] h-[44px] justify-center flex items-center rounded-xl"
      :class="{ 'bg-black text-white': $route.query.page === '5' }"
    >
      5
    </NuxtLink>
    <NuxtLink
      :to="`/?page=${$route.query.page ? Number($route.query.page) + 1 : 2}`"
      class="w-[44px] h-[44px] justify-center flex items-center rounded-xl"
      v-if="$route.query.page !== '5'"
    >
      <svg
        class="-mt-1"
        width="24"
        height="24"
        viewBox="0 0 24 24"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M9.5 7.5L14.5 12.5L9.5 17.5"
          stroke="#494949"
          stroke-width="1.3"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
      </svg>
    </NuxtLink>
  </div>
</template>
