<template>
  <div>
    <div>
      <div v-if="loading">Loading...</div>
      <div v-if="error">{{ error }}</div>

      <div>{{ data?.quote }}</div>
      <div>{{ data?.author }}</div>
    </div>
    <div>
      <button v-if="!disabledBtn" @click="handleClick">Fetch</button>
      <p v-if="disabledBtn">disabled</p>
    </div>
  </div>
</template>
<script setup lang="ts">
import { defineProps, ref } from "vue";

interface objectAPI {
  author: string;
  quote: string;
}
interface linkAPI {
  link: string;
}
const props = defineProps<linkAPI>();
const data = ref<objectAPI | null>(null);
const error = ref<string | null>(null);
const loading = ref<boolean>(true);
const disabledBtn = ref<boolean>(false);

function handleClick() {
  fetchData();
}
const fetchData = async () => {
  disabledBtn.value = true;
  try {
    const response = await fetch(props.link);

    if (!response.ok) {
      throw new Error("not ok");
    }
    data.value = await response.json();
  } catch (err) {
    error.value = "failt to load data";
  } finally {
    loading.value = false;
    disabledBtn.value = false;
  }

  console.log(data.value);
};
</script>

<style>
button {
  color: darkblue;
  background-color: lightblue;
  border: 1px solid blue;
}
</style>
