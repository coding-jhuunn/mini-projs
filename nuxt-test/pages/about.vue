<template>
  <div>
    <h1>about</h1>
    {{ data }}
  </div>
</template>

<script setup>
const { data } = await useFetch("/api/exone?name=mario", {
  method: "post",
  body: {
    age: 30,
  },
});
</script>
