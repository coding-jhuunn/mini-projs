<script setup>
defineProps({
  todoListProps: Object,
});
const showIndex = (index) => {
  console.log(index);
};
</script>

<template>
  <div>
    <h3>{{ todoListProps.title }}</h3>
    <button @click="showIndex(todoListProps.title)">key</button>
  </div>
</template>
