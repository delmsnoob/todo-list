<template>
    <div class="todo-container">
        <div class="todo-item" v-bind:class="{'is--completed': todo.completed}">
            <label class="todo-title">
                <input type="checkbox" v-on:change="markComplete">
                <div class="checkmark"></div>                
                <h3>{{ todo.title }}</h3>
            </label>
        </div>
        <div class="action-container">
            <!-- <i class="action far fa-edit"></i> -->
            <i class="action far fa-trash-alt"></i>
        </div>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
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
    padding: 1px 8px 1px 60px;
    display: flex;
    align-items: center;
    width: 70%;
}

.is--completed {
    text-decoration: line-through;
}

.todo-title {
    display: flex;
    align-items: center;
    padding-right: 20px;
}

.todo-title input {
    position: absolute;
    opacity: 0;
}

.checkmark {
    border-radius: 25px;
    background: #e0e0e0;
    position: relative;
    width: 22px;
    top: 0;
    left: 0;
    height: 1.3em;
    width: 1.3em;
}

.todo-title input:checked .checkmark {
    background-color: #000;
    border-radius: 25px;
    transition: 0.15s;
}

.checkmark::after {
    content: "";
    position: absolute;
    display: none;
}

.todo-title input:checked .checkmark::after{
    display: block;
}

.todo-title .checkmark::after {
    left: 0.45em;
 top: 0.25em;
 width: 0.25em;
 height: 0.5em;
 border: solid white;
 border-width: 0 0.15em 0.15em 0;
 transform: rotate(45deg);
}

/* input[type="checkbox"] {
    transform: scale(1.4);
    width: 10px;
    margin: 0;
    margin-right: 12px;
    margin-left: 6px;
    margin-bottom: 5px;
    opacity: 1;
}

input[type="checkbox"]:checked {
    background-color: #000;
 border-radius: 25px;
 transition: 0.15s;
}

input[type="checkbox"]::after {
    display: block;
} */

.action-container {
    display: inline;
    cursor: pointer;
    font-size: 20px;
}

.action {
    padding-right: 10px;
}
</style>
https://cssbuttons.io/detail/martinval9/wise-elephant-23