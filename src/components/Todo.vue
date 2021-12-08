<template>
    <div class="todo-container">
        <div class="todo-item" v-bind:class="{'is--completed': todo.completed}">
            <label class="todo-title">
                
                <div class="checkmark">
                    <input type="checkbox" v-on:change="markComplete">
                </div>
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

.checkmark {
    border-radius: 100px;
    background: #e0e0e0;
    position: relative;
    margin-right: 20px;
    width: 22px;
}

.checkmark::after {
    content: "";
    position: absolute;
    display: none;
}

input[type="checkbox"] {
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
 /* transition: 0.15s; */
}

input[type="checkbox"]::after {
    display: block;
}

.action-container {
    display: inline;
    cursor: pointer;
    font-size: 20px;
}

.action {
    padding-right: 10px;
}
</style>