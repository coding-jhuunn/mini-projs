<template>
  <div class="flex justify-center mb-5 p-5">
    <!-- text-xs sm:text-sm md:text-base lg:text-lg -->
    <form
      class="p-5 w-[300px] shadow-xl rounded-2xl"
      @submit.prevent="submitForm"
    >
      <div class="mb-1 flex flex-col justify-between h-11">
        <input
          placeholder="Input Here ..."
          v-model="titleTask"
          type="text"
          class="block w-full bg-gray-50 p-1 pl-2 focus:outline-none focus:ring-1 focus:ring-blue-500 rounded-lg"
          @input="handleChangeInput"
        />
        <p class="ml-1 text-red-500 text-[10px]" v-show="errorShow">
          {{ errorMessage }}
        </p>
      </div>
      <div>
        <div class="flex mb-2 pl-1">
          <input v-model="priorityTask" type="checkbox" class="mr-1" />
          <label class="text-sm md:text-base">Priority</label>
        </div>
        <div class="flex justify-center items-center w-100%">
          <button
            class="w-[150px] text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
          >
            Submit
          </button>
        </div>
      </div>
    </form>
  </div>
</template>
<script setup>
import { ref, defineEmits } from "vue";

const emit = defineEmits(["updateTodoList"]);
const titleTask = ref("");
const priorityTask = ref(false);
const errorShow = ref(false);
const errorMessage = ref("");

// handle error message input empty to toggle
function handleChangeInput(event) {
  errorShow.value = false;
}

const submitForm = () => {
  if (titleTask.value.length === 0) {
    errorMessage.value = "Please enter a value";
    errorShow.value = true;
  } else {
    errorShow.value = false;
    emit("updateTodoList", {
      id: Date.now(),
      title: titleTask.value,
      priorityTask: priorityTask.value,
    });
    titleTask.value = "";
    priorityTask.value = false;
  }
};
</script>
