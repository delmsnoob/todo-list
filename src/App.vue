<template>
  <main>
    <div class="main__container">
      <Header title="Website todo"/>
      <!-- <AddTodo /> -->
      <div class="main__body">
        <Todos
          v-bind:todos="todos"
          v-on:delete-todo="deleteTodo"
          v-on:add-todo="addTodo"
        />
      </div>
    </div>
  </main>
</template>

<script>
import Header from './components/Header'
import Todos from './components/Todos'
import AddTodo from './components/AddTodo'

export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Styleguide creation",
          completed: null
        },
        {
          id: 2,
          title: "Send wireframes",
          completed: null
        },
        {
          id: 3,
          title: "Readability About page",
          completed: null
        },
        {
          id: 4,
          title: "Check color contrast",
          completed: null
        }
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      if (confirm('Are you sure?')) {
        this.todos = this.todos.filter(todo => todo.id !== id)
      }
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
  margin: auto;
}

main {
  display: flex;
  height: 90vh;
  justify-content: center;
  align-items: center;
  
}

.main__container {
  margin: 10px;
  width: 500px;
}

.main__body {
  margin-top: 20px;
  background: #fff;
  min-height: 105px;
}
</style>
