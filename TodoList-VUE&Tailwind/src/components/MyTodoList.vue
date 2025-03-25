<script setup>
import { defineEmits } from "vue";
import MyItemTodo from "./MyItemTodo.vue";

const emit = defineEmits(["deleteItemTodo", "toggleItemTodo"]);

const deleteItemTodo = (index) => {
  emit("deleteItemTodo", index);
};
const toggleItemTodo = (index) => {
  emit("toggleItemTodo", index);
};

const props = defineProps({
  myTodoList: Array,
  toggleTodoList: Function,
  IsSorted: Boolean,
});
</script>
<template>
  <div class="flex justify-center items-center">
    <div class="w-[300px] sm:w-[400px] md:w-[500px]">
      <div class="flex justify-between text-sm md:text-base mb-2 border-b-2">
        <div c>LIST TO DO</div>
        <div>
          <button
            @click="toggleTodoList"
            class="hover:scale-150 cursor-pointer"
          >
            <i v-show="IsSorted" class="bx bx-sort"></i>
            <i v-show="!IsSorted" class="bx bx-shuffle"></i>
          </button>
        </div>
      </div>
      <MyItemTodo
        v-for="item in myTodoList"
        :key="item.id"
        :task="item"
        @deleteItemTodo="deleteItemTodo"
        @toggleItemTodo="toggleItemTodo"
      ></MyItemTodo>
    </div>
  </div>
</template>
