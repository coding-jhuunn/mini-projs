<template>
  <div>
    <ItemTodo v-for="(list, index) in todoList" :key="index" :todoListProps="list"></ItemTodo>
  </div>
</template>
<script setup>
import ItemTodo from "./ItemTodo.vue";

const todoList = [
  {
    title: "todo",
    priority: true,
  },
  {
    title: "todo2",
    priority: true,
  },
  {
    title: "todo3",
    priority: false,
  },
  {
    title: "todo4",
    priority: false,
  },
];
</script>
