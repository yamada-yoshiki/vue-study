<template>
  <div class="h-4/5 w-full overflow-auto">
    <draggable @end="listChanged()" v-model="todos" item-key="id" draggable=".item">
      <template #item="{element, index}">
        <div :class="isCompleted(element)" class="h-10 bg-gray-900 rounded-lg flex items-center item mt-3">
          <input @click="$emit('onCheckbox', element)" :checked="element.completed" id="teal-checkbox" type="checkbox" value="" class="w-4 h-4 text-teal-600 bg-gray-100 border-gray-300 rounded focus:ring-teal-500 dark:focus:ring-teal-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600 mx-3">
          <div class="text-area whitespace-nowrap overflow-x-scroll">
            {{ element.text }}
          </div>
          <button @click="index => $emit('onDelete', index)" class="ml-auto bg-red-600 hover:bg-red-700 text-white font-bold py-2 px-4 rounded-lg">
            <TrashCanIcon />
          </button>
        </div>
      </template>
    </draggable>
  </div>
</template>

<script>
import draggable from 'vuedraggable'
import TrashCanIcon from 'vue-material-design-icons/TrashCanOutline.vue';

export default {
  components: {
    draggable,
    TrashCanIcon
  },
  props: {
    todoList: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      todos: this.todoList
    }
  },
  methods: {
    listChanged() {
      this.$emit('listChanged', this.todos)
    },
    isCompleted(todo) {
      return todo.completed ? "text-gray-500" : "text-white"
    }
  }
}
</script>

<style scoped>
	::-webkit-scrollbar{
   width: 5px;
}
::-webkit-scrollbar-track{
   background-color: rgb(55 65 81);
}
::-webkit-scrollbar-thumb{
   background-color: #868686;
}
.text-area::-webkit-scrollbar {  /* Chrome, Safari 対応 */
      display:none;
  }
</style>

