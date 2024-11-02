<template>
    <button
      class="cursor-pointer w-full transition-all bg-sky-600 text-white px-6 py-2 rounded-lg
             border-blue-600 border-b-[4px] hover:brightness-110"
      @click="onClick"
    >
      <slot>Button</slot>
    </button>
  </template>
  
  <script>
  export default {
    name: 'Button',
    props: {
      onClick: {
        type: Function,
        required: false,
      },
    },
  };
  </script>