<template>
    <div class="todo__wrapper">
      <div class="todo__item">
        <label class="todo__title" v-bind:class="{'todo__item--check': todo.completed}">
          <input type="checkbox" v-on:change="markTodo">
          <div class="checkmark"></div>
          {{ todo.title }}
        </label>
      </div>
      <div class="deleteTodo__wrapper">
        <i 
          @click="$emit('delete-todo', todo.id)"
          v-bind:class="{'todo__item--delete': todo.completed}"
          class="delete__icon far fa-trash-alt"
        >
        </i>
      </div>
    </div>
</template>

<script>
export default {
  name: 'Todo',
  props: ["todo"],
  methods: {
    markTodo() {
      this.todo.completed = !this.todo.completed
    }
  }
}
</script>

<style scoped>
.todo__wrapper {
  display: flex;
  width: 100%;
  align-items: center;
  justify-content: space-between;
}

.todo__item {
  /* padding: 0 8px 0 60px; */
  align-items: flex-start;
  display: inline-flex;
  width: 100%;
}

.todo__item--check {
  text-decoration: line-through;
}

.todo__title {
  display: flex;
  color: #505050;
  font-weight: bold;
  font-size: 1.2em;
  cursor: pointer;
  user-select: none;

}

.deleteTodo__wrapper {
  font-size: 1.2em;
  /* float: ;   */
}

.delete__icon {
  cursor: pointer;
  display: none;
}

.todo__item--delete {
  display: block;
}
</style>
