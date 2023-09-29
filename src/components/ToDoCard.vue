<template>
  <div :class="isCompleted" class="h-10 bg-gray-900 rounded-lg flex items-center">
    <input @click="$emit('onCheckbox', todo)" :checked="todo.completed" id="teal-checkbox" type="checkbox" value="" class="w-4 h-4 text-teal-600 bg-gray-100 border-gray-300 rounded focus:ring-teal-500 dark:focus:ring-teal-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600 mx-3">
    <div class="text-area whitespace-nowrap overflow-x-scroll">
      {{ todo.text }}
    </div>
    <button @click="$emit('onDelete', todo)" class="ml-auto bg-red-600 hover:bg-red-700 text-white font-bold py-2 px-4 rounded-lg">
      ✖️
    </button>
  </div>
</template>

<script>

export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  computed: {
    isCompleted() {
      return this.todo.completed ? "text-gray-500" : "text-white"
    }
  }
}
</script>

<style scoped>
  .text-area::-webkit-scrollbar {  /* Chrome, Safari 対応 */
      display:none;
  }
</style>
