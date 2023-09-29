<template>
  <div class="h-4/5 w-full overflow-auto">
    <draggable @end="listChanged()" v-model="todos" item-key="id" draggable=".item">
      <template #item="{element, index}">
        <ToDoCard
        @onCheckbox="(todo) => $emit('onCheckbox', todo)"
        @onDelete="todo => $emit('onDelete', todo)"
        :key="element.id" 
        :todo="element" 
        class="mt-3 item" 
        />
      </template>
    </draggable>
  </div>
</template>

<script>
import ToDoCard from '@/components/ToDoCard.vue'
import draggable from 'vuedraggable'

export default {
  components: {
    ToDoCard,
    draggable
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
</style>

