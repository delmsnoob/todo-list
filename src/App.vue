<template>
  <main>
    <div class="main__wrapper">
      <div class="content__header">
        <Header text="Website Todo"/>
      </div>
      <div class="body__wrapper">
        <transition name="fade">
          <Todos
            v-if="showAddTodo"
            v-bind:todos="todos"
            v-on:delete-todo="deleteTodo"
          />
          <AddTodo
            v-if="!showAddTodo"
            @add-todo="addTodo"
          />
        </transition>
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
      completed: false
    },
    {
      id: 2,
      title: "Send wireframes",
      completed: true
    },
    {
      id: 3,
      title: "Readability About page",
      completed: false
    },
    {
      id: 4,
      title: "Check color contrast",
      completed: true
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
    addTodo(todo) {
      this.todos = [...this.todos, todo]
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
  justify-content: center;
  align-items: center;
  height: 90vh;
  overflow: hidden;
}

button, input[type="text"] {
  font-family: 'Open Sans';
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
  min-height: 150px;
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

.fade-enter-active, .fade-leve-active {
  transition: opacity 1s;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>