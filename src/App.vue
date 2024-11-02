<template>
  <div class="min-h-screen flex items-center justify-center bg-sky-950">
    <div class="w-full max-w-md p-6 bg-sky-50 shadow-2xl rounded-xl">
      <div class="w-full max-w-md flex justify-center gap-5 pb-5">
        <ListsIcon />
        <h1 class="text-xl font-bold">To-Do List</h1>
        <!-- <CompleteButton /> -->
      </div>
      <TodoList />
    </div>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue';
// import CompleteButton from './components/CompleteButton.vue';
import ListsIcon from './components/Icons/lists.vue';

export default {
  name: 'App',
  components: {
    TodoList,
    ListsIcon,
    // CompleteButton,
  },
};
</script>