<template>
    <form @submit.prevent="addNewTodo">
        <h2>{{ msg }}</h2>
        <label for="title">New Todo</label>
        <input v-model="newTodo" type="text" name="newTodo" />
        <button>Add</button>
        <!-- <p>{{ todos }}</p> -->
    </form>
    <ul>
        <li v-for="(todo, index) in todos" v-bind:key="todo.id">
            <input type="checkbox" v-model="todo.done" />
            <h4 :class="{ done: todo.done }">{{ todo.value }}</h4>
            <button @click="removeTodo(index)">X</button>
        </li>
    </ul>
    <button @click="markAllDone">Mark All Done</button>
</template>

<script>
import { ref } from "vue"

export default {
    name: "NewTodoForm",
    props: {
        msg: String,
    },

    setup() {
        const newTodo = ref("")
        const todos = ref([])

        function addNewTodo() {
            todos.value.push({
                id: Date.now(),
                done: false,
                value: newTodo.value,
            })
            console.log(newTodo.value)
            newTodo.value = ""
        }

        function removeTodo(index) {
            todos.value.splice(index, 1)
        }

        function markAllDone() {
            todos.value.map((todo) => (todo.done = true))
        }

        return {
            addNewTodo,
            newTodo,
            todos,
            removeTodo,
            markAllDone,
        }
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
li {
    display: flex;
    justify-content: center;
    flex-direction: row;
    align-items: center;
}
li h4 {
    min-width: 20vw;
    text-align: left;
    margin-left: 10px;
}
.done {
    text-decoration: line-through;
}
</style>
