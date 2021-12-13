<template>
  <form class="add__todo__form" @submit="onSubmit">
    <input type="text" name="title" v-model="title" placeholder="What's on your mind">
    <input type="checkbox" name="completed" v-model="completed" class="is-completed">
  </form>
</template>

<script>
export default {
  name: 'AddTodo',
  data() {
    return {
      title: '',
      completed: false
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault()

      if (!this.title) {
        alert('Please add a new task')
        return
      }

      const newTodo = {
        title: this.title,
        completed: this.completed
      }

      console.log(newTodo)

      this.title = ''
      this.reminder = false
    }
    
  }
}
</script>

<style>
.add__todo__form {
  display: flex;
  justify-content: center;    
  align-items: center;
  margin-top: 20px;
}

.add__todo__form input[type="text"] {
  font-size: 1.1em;
  padding: 15px 50px 15px 20px;
  border: 2px solid #b292da;
  border-radius: 20px;
  width: 100%;
  color: rgb(60, 58, 58);
}

.add__todo__form input[type="checkbox"] {
  display: none;
}

</style>