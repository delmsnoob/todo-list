<template>
  <form @submit="onSubmit" class="addtodo__wrapper">
    <input type="text" v-model="newTodo" class="new__todo__title">
    <button type="submit">Save</button>
  </form>
</template>

<script>
export default {
  name: 'AddTodo',
  data() {
    return {
      newTodo: ''
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault()

      if (!this.text) {
        alert('Please add todo')
        return
      }

      const newTodo = {
        title: this.newTodo,
        completed: null
      }

      this.$emit('add-todo', newTodo)

      this.newTodo = ''
    }
  }
}
</script>