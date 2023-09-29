<template>
  <div class="flex justify-between">
    <input v-model="text" type="text" class="w-3/4 h-10 rounded-lg bg-gray-900 px-3 text-white" placeholder="Type here"/>
    <button @click="onAddButton()" :disabled="isBlank" :class="[isBlank ? 'bg-gray-500' : 'bg-teal-600 hover:bg-teal-700']" class="ms-10 text-white font-bold py-2 px-4 rounded-lg">
      Add
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      text: ""
    }
  },
  methods: {
    onAddButton() {
      this.$emit('todoAdded', this.text)
      this.text = ''
    }
  },
  computed: {
    isBlank() {
      return this.text.length === 0
    }
  }
}
</script>

<style scoped>
</style>

