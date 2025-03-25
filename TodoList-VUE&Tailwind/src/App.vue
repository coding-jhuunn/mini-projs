<script setup>
import { computed, ref } from "vue";
import MyHeader from "./components/MyHeader.vue";
import MyForm from "./components/MyForm.vue";
import MyTodoList from "./components/MyTodoList.vue";

const todolist = ref([
  {
    id: 1,
    title: "Clean my Room",
    priorityTask: true,
  },
  {
    id: 2,
    title: "Read books",
    priorityTask: false,
  },
  {
    id: 3,
    title: "Serve Files",
    priorityTask: true,
  },
  {
    id: 4,
    title: "Take a bath",
    priorityTask: false,
  },
]);
const IsSorted = ref(true);
const sortTask = computed(() => {
  return [...todolist.value].sort((a, b) => {
    return IsSorted.value
      ? a.priorityTask - b.priorityTask
      : b.priorityTask - a.priorityTask;
  });
});

const updateTodoList = (item) => {
  todolist.value.push(item);
};
const deleteItemTodo = (item) => {
  todolist.value = todolist.value.filter((task) => task.id !== item);
};
const toggleItemTodo = (item) => {
  console.log("toggle");
  const task = todolist.value.find((task) => task.id === item);
  if (task) {
    task.priorityTask = !task.priorityTask;
  }
};
function toggleTodoList() {
  IsSorted.value = !IsSorted.value;
  console.log("toggled");
}
</script>

<template>
  <div class="bg-blue-50 min-h-screen">
    <MyHeader></MyHeader>

    <MyForm @updateTodoList="updateTodoList"></MyForm>

    <MyTodoList
      :IsSorted="IsSorted"
      :myTodoList="IsSorted ? todolist : sortTask"
      @deleteItemTodo="deleteItemTodo"
      @toggleItemTodo="toggleItemTodo"
      :toggleTodoList="toggleTodoList"
    ></MyTodoList>
  </div>
</template>
