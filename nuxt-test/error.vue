<template>
  <div class="mt-7 max-w-sm mx-auto text-center">
    <p class="mt-7 text-7xl font-bold">{{ error.StatusCode }}</p>
    <p class="mt-7 text-6xl">ooop</p>
    <p class="mt-7">{{ error.message }}</p>
    <button class="btn my-7" @click="handleClearError">Go Home ...</button>
  </div>
</template>

<script setup>
defineProps(["error"]);
const handleClearError = () => clearError({ redirect: "/" });
</script>

<style lang="scss" scoped></style>
