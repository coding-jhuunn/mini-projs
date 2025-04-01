<template>
  <div class="card text-center">
    <img :src="product.image" alt="" />
    <p class="font-bold text-gray-500 m-5 truncate">{{ product.title }}</p>
    <nuxt-link :to="`/products/${product.id}`"
      ><p class="btn my-4">view details</p></nuxt-link
    >
  </div>
</template>

<script setup>
import { defineProps } from "vue";
const { product } = defineProps(["product"]);
</script>
<style lang="scss" scoped></style>
