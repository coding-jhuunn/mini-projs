<template>
  <div class="grid grid-cols-4 gap-5">
    <div v-for="p in products" :key="`${p.id}`">
      <ProductCard :product="p"></ProductCard>
    </div>
  </div>
</template>

<script setup>
import { ProductCard } from "#components";
definePageMeta({
  layout: "products",
});
// fetch the products
const { data: products } = await useFetch("https://fakestoreapi.com/products");

useHead({
  title: "Nnuxt Products",
  meta: [
    {
      name: "description",
      content: "nuxt products",
    },
  ],
});
</script>

<style lang="scss" scoped></style>
