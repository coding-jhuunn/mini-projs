<template>
  <div>
    <MyForm @submit-item="updateItem"></MyForm>
    <ListTodo :message="messageFromA"></ListTodo>
  </div>
</template>

<script setup>
import MyForm from "./MyForm.vue";
import ListTodo from "./ListTodo.vue";
import { ref } from "vue";

const messageFromA = ref({});

const updateItem = (msg) => {
  messageFromA.value = msg;
};
</script>
