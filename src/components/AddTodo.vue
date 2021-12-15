<template>
  <form @submit="onSubmit" class="addtodo__wrapper">
    <div class="title__wrapper">
      <input type="text" v-model="newTodo" placeholder="What's on your mind?">
      <input type="checkbox" v-model="status" hidden>
    </div>
    <div class="btn__wrapper">
      <button type="submit">Save</button>
    </div>
  </form>
</template>

<script>
export default {
  name: 'AddTodo',
  data() {
    return {
      newTodo: '',
      status: false
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault()

      if (!this.newTodo) {
        alert('Please add todo')
        return
      }

      const newTodo = {
        title: this.newTodo,
        completed: this.status
      }

      this.$emit('add-todo', newTodo)

      this.newTodo = ''
      this.status = false
    }
  },
}
</script>

<style scoped>
.addtodo__wrapper {
  display: flex;
  width: 380px;
  height: 100px;
  justify-content: center;
  align-items: center;
}

.title__wrapper input[type="text"] {
  align-items: center;
  justify-content: center;
  width: 280px;
  outline: none;
  padding-left: 10px;
  height: 50px;
  border: 2px solid #af7eeb;
  border-radius: 10px;
  font-size: 1em;
}

.btn__wrapper {
  display: flex;
  margin-left: 10px;
  width: 100%;
}

button {
  align-items: center;
  display: flex;
  justify-content: center;
  width: 100%;
  height: 56px;
  background: #af7eeb;
  color: #fff;
  font-size: 1em;
  border: 1px solid transparent;
  border-radius: 10px;
  box-shadow: 1px 1px 5px 1px rgba(0,0,0,0.51);
}

button:hover{
  background: #c198eb;
}
</style>