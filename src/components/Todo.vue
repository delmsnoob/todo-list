<template>
    <div class="todo-item" v-bind:class="{'is--completed': todo.completed}">
        <label class="todo-title">
            <input type="checkbox" name="todo-checkbox" class="item--checkbox" v-on:change="markComplete">
            <h3>
                {{ todo.title }}
                <div class="todo-item__delete--icon">
                    <i class="delete-icon far fa-trash-alt"></i>
                </div>
            </h3>
        </label>
        
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
.todo-item {
    margin: 30px auto;
    box-shadow: .5px 1px 5px rgba(70, 49, 49, 0.57);
    padding: 20px;
    border-radius: 5px;

}

.is--completed {
    text-decoration: line-through;
}

.todo-title {
    display: flex;
}

.item--checkbox {
    /* height: 20px;
    width: 25px; */
    transform: scale(1.8);
    /* margin: 10px; */
}

input[type="checkbox"] {
    margin-right: 20px;
}

.todo-item__delete--icon {
    cursor: pointer;
    font-size: 20px;
    /* padding: 20px; */
    display: inline;
    float: right;
    justify-content: right;
    
}
</style>