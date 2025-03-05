<script setup>
defineProps({
  todoListProps: Object,
});
</script>

<template>
  <div>
    <h3>{{ todoListProps.title }}</h3>
  </div>
</template>
