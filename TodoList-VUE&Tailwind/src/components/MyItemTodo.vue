<template>
  <div
    class="flex justify-between items-center mb-2 p-1 rounded-lg shadow-sm"
    :class="task.priorityTask ? 'bg-green-200' : 'bg-orange-200'"
  >
    <div class="flex p-1">
      <div class="flex ju items-center mr-1">
        <button
          @click="toggleItem(task.id)"
          class="hover:scale-150 cursor-pointer flex justify-items-center"
        >
          <i v-show="task.priorityTask" class="bx bxs-star"></i>
          <i v-show="!task.priorityTask" class="bx bxs-star-half"></i>
        </button>
      </div>
      <div class="flex justify-center items-center">
        {{ task.title }}
      </div>
    </div>
    <div>
      <button @click="deleteItem(task.id)">
        <i class="bx bxs-minus-circle hover:scale-150 cursor-pointer"></i>
      </button>
    </div>
  </div>
</template>

<script setup>
import { defineEmits } from "vue";

defineProps(["task"]);
const emit = defineEmits(["deleteItemTodo", "toggleItemTodo"]);

const deleteItem = (index) => {
  console.log(index);
  emit("deleteItemTodo", index);
};
const toggleItem = (index) => {
  emit("toggleItemTodo", index);
};
</script>
