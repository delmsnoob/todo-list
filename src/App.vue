<template>
  <main>
    <div class="main__wrapper">
      <div class="content__header">
        <Header text="Website Todo"/>
      </div>
      <div class="body__wrapper">
        <div v-show="showAddTodo">
          <Todos
            v-bind:todos="todos"
            v-on:delete-todo="deleteTodo"
          />
        </div>
        <div v-show="!showAddTodo">
          <AddTodo />
        </div>
      </div>
      <div class="btn__wrapper">
        <ToggleAddTodo
          @toggle-click="toggleShowAddTodo"
          :text="showAddTodo ? 'New Task' : 'Close'" 
          class="btn"
        />
      </div>
      </div>
  </main>
</template>

<script>
import Header from './components/Header'
import Todos from './components/Todos'
import AddTodo from './components/AddTodo'
import ToggleAddTodo from './components/ToggleAddTodo'

export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo,
    ToggleAddTodo,
  },
  data() {
    return {
      showAddTodo: true,
      "todos": [
    {
      id: 1,
      title: "Styleguide creation",
      completed: true
    },
    {
      id: 2,
      title: "Send wireframes",
      completed: true
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
    toggleShowAddTodo() {
      this.showAddTodo = !this.showAddTodo
    },
    deleteTodo(id) {
      if (confirm('Are you sure?')) {
        this.todos = this.todos.filter(todo => todo.id !== id)
      }
    },
    addTodo() {

    },
    async fetchTodos() {
      const res = await fetch('http://localhost:4000/todos')

      const data = await res.json()

      return data
    },
    async fetchTodo(id) {
      const res = await fetch(`api/todos/${id}`)

      const data = await res.json()

      return data
    },
    async created() {
      this.todos = await this.fetchTodos()
    }
  }
}
</script>

<style>
body {
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

.main__wrapper {
  width: 31.25rem;
  margin: 10px;
}

.body__wrapper {
  display: flex;
  /* justify-content: center; */
  align-items: center;
  /* text-align: left; */
  margin-top: 20px;
  background: #fff;
  min-height: 200px;
  padding: 40px 60px 40px 60px;
}

.btn__wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}

.btn {
  font-family: 'Open Sans';
  position: absolute;
  font-weight: bold;
  font-size: 1.2em;
  width: 200px;
  height: 60px;
  color: #fff;
  background: #af7eeb;
  border: 1px solid transparent;
  border-radius: 30px;
  box-shadow: 1px 1px 5px 1px rgba(0,0,0,0.51);
  cursor: pointer;
  }

.btn:hover {
  background: #c198eb;
}

.fas {
  color: black;
}
</style>