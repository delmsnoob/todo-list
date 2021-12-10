<template>
    <div class="todo-container">
        <div class="todo-item" v-bind:class="{'is--completed': todo.completed}">
            <label class="todo-title">
                <input type="checkbox" v-on:change="markComplete">
                <div class="checkmark"></div>                
                {{ todo.title }}
            </label>
        </div>
        <div class="action-container">
            <i @click="$emit('del-todo', todo.id)" class="action far fa-trash-alt" v-bind:class="{'todo-completed': todo.completed}"></i>
        </div>
    </div>
</template>

<script>
export default {
    name: "Todo",
    props: ["todo"],
    methods: {
        markComplete() {
            this.todo.completed = !this.todo.completed
        }
    }
}
</script>

<style scoped>
.todo-container {
    display: flex;
    align-items: center;
}
.todo-item {
    padding: 0 8px 0 60px;
    width: 70%;
}

.is--completed {
    text-decoration: line-through;
}

.todo-title {
    display: flex;
    align-items: center;
    color: rgb(95, 92, 92);
    font-weight: bolder;
    font-size: 1.2em;
    cursor: pointer;
    margin: 20px 0 20px -5px;
}

/* hide default input checkbox */
.todo-title input {
    position: relative;
    opacity: 0;
}

.checkmark {
    border-radius: 25px;
    background: #e0e0e0;
    position: relative;
    width: 1.3em;
    top: 0;
    left: 0;
    height: 1em;
    width: 1em;
    margin-right: 25px;
    border: 2px solid #9c7ac5;
}

.todo-title input:checked ~ .checkmark {
    background: #AF7EEB;
    border-radius: 25px;
    transition: 0.2s;
    border: 2px solid #524d4d;
}

.checkmark:after {
    content: "";
    position: absolute;
    display: none;
}

.todo-title input:checked ~ .checkmark::after{
    display: block;
}

/* adds checkmark after title */
/* .todo-title .checkmark::after {
    left: 0.32em;
    top: 0.15em;
    width: 0.25em;
    height: 0.5em;
    border: solid white;
    border-width: 0 0.15em 0.15em 0;
    transform: rotate(45deg);
} */

.action-container {
    font-size: 20px;
}

.action {
    padding-right: 10px;
    display: none;
    cursor: pointer;
}

.todo-completed {
    display: block;
    transition: .2s;
}
</style>