<template>
  <div class="w-full h-full flex justify-center items-center">
    <div class="w-4/5 h-4/5 bg-gray-700 rounded-lg">
      <div class="h-full w-full py-10 px-10">
        <AddNewToDoArea @todoAdded="(text) => addTodo(text)"></AddNewToDoArea>
        <ToDoListArea @onCheckbox="(todo) => toggleCompleted(todo)" @onDelete="(todo) => deleteTodo(todo)" :todoList="todoList" class=" mt-10"/>
      </div>
    </div>
  </div>
</template>

<script>
import AddNewToDoArea from '../components/AddNewToDoArea.vue'
import ToDoListArea from '../components/ToDoListArea.vue'

let id = 0
export default {
  components: {
    AddNewToDoArea,
    ToDoListArea
  },
  data() {
    return {
      todoList: [
      {id: id++, text: 'スーパー行く', completed: false},
      {id: id++, text: '宿題やる', completed: true}
      ]
    }
  },
  methods: {
    addTodo(text) {
      this.todoList.push(
        {id: id++, text: text, completed: false}
      )
    },
    toggleCompleted(todo) {
      this.todoList.forEach((t) => {if (t === todo) {
        t.completed = !t.completed
      }})
    },
    deleteTodo(todo) {
      this.todoList = this.todoList.filter(data => data !== todo)
    }
  }
}
</script>

<style scoped>
</style>
