<template>
    <div>
      <form @submit.prevent="addTask" class="mb-4">
        <input
          v-model="newTask"
          type="text"
          placeholder="Add a new task..."
          class="w-full px-4 py-2 border border-gray-300 rounded-lg mb-2 focus:outline-none focus:border-blue-600"
        />
        <Button :onClick="addTask">Add Task</Button>
      </form>
  
      <ul class="space-y-2">
        <li
          v-for="(task, index) in tasks"
          :key="index"
          class="flex justify-between items-center p-3 bg-gray-100 rounded-lg shadow-sm"
        >
          <span :class="{ 'line-through text-gray-600': task.completed }">{{ task.text }}</span>
          <div class="flex space-x-2">
            <button @click="toggleTask(index)" class="bg-green-500 py-2 px-2 rounded-md text-white shadow-lg hover:bg-green-700">
              <component :is="task.completed ? 'UndoIcon' : 'CompleteIcon'"/>
            </button>
            <button @click="removeTask(index)" class="bg-red-500 py-2 px-2 rounded-md text-white shadow-lg hover:bg-red-700">
              <DeleteIcon />
            </button>
          </div>
        </li>
      </ul>
    </div>
  </template>
<script>
import { ref } from 'vue';
import Button from './button.vue';
import CompleteIcon from './Icons/complete.vue'
import UndoIcon from './Icons/undo.vue'
import DeleteIcon from './Icons/delete.vue'

export default {
  name: 'TodoList',
  components: {
    Button,
    CompleteIcon,
    UndoIcon,
    DeleteIcon,
  },
  setup() {
    const tasks = ref([]);
    const newTask = ref('');

    function addTask() {
      if (newTask.value.trim() !== '') {
        tasks.value.push({ text: newTask.value, completed: false });
        newTask.value = '';
      }
    }

    function toggleTask(index) {
      tasks.value[index].completed = !tasks.value[index].completed;
    }

    function removeTask(index) {
      tasks.value.splice(index, 1);
    }

    return {
      tasks,
      newTask,
      addTask,
      toggleTask,
      removeTask,
    };
  },
};
</script>