<script setup="ts">
// https://quotes-api-self.vercel.app/quote link of API

import TitleCard from "./components/TitleCard.vue";
import FetchApi from "./components/FetchApi.vue";
const linkAPI = "https://quotes-api-self.vercel.app/quote";
</script>

<template>
  <TitleCard></TitleCard>
  <FetchApi :link="linkAPI" />
</template>

<style scoped></style>
