<template>
  <div class="container">
    <div class="container__header">
      <Header title="Website todo"/>
      <div class="container__body">
        <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" v-on:add-todo="addTodo"/>
      </div>
    </div>
    
  </div>
</template>

<script>
import Header from './components/Header'
import Todos from './components/Todos'

export default {
  name: 'App',
  components: {
    Header,
    Todos,
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Styleguide creation",
          schedule: "March",
          completed: null
        },
        {
          id: 2,
          title: "Send wireframes",
          schedule: "March",
          completed: null
        },
        {
          id: 3,
          title: "Readability About page",
          schedule: "March",
          completed: null
        },
        {
          id: 4,
          title: "Check color contrast",
          schedule: "March",
          completed: null
        }
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    addTodo(id) {
      console.log(asdasd)
    }
  }
}
</script>

<style>

body {
  user-select: none;
  background: #E3E9FF;
  font-family: 'Open Sans';
}

.container {
  display: grid;
  height: 90vh;
  justify-content: center;
  align-items: center;
  margin-right: auto;
  margin-left: auto;
}

.container__header {
  margin-right: auto;
  margin-left: auto;
}

.container__body {
  display: block;
  width: 100%;
  margin-top: 20px;
  background: #fff;
  /* justify-content: space-between; */
  align-items: center;
  min-height: 105px;
}
</style>
