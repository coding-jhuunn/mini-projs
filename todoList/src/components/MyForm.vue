<template>
  <form @submit.prevent="submitForm">
    <input type="text" class="border-2" id="title" v-model="itemData.title" />
    <input type="checkbox" id="priority" v-model="itemData.priority" />
    <button type="submit">Submit</button>
  </form>
</template>

<script setup>
import { ref, defineEmits } from "vue";

const itemData = ref({
  title: "",
  priority: false,
});

const emit = defineEmits(["submit-item"]);

const submitForm = () => {
  emit("submit-item", itemData.value);
};
</script>
