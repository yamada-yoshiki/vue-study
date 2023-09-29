<template>
  <div class="h-4/5 w-full overflow-auto">
    <ToDoCard
      @onCheckbox="(todo) => $emit('onCheckbox', todo)"
      @onDelete="todo => $emit('onDelete', todo)"
      v-for="todo in todoList" 
      :key="todo.id" 
      :todo="todo" 
      class="mt-3" 
    />
  </div>
</template>

<script>
import ToDoCard from '@/components/ToDoCard.vue'

export default {
  components: {
    ToDoCard
  },
  props: {
    todoList: {
      type: Array,
      required: true
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

