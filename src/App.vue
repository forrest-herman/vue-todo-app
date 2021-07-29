<template>
    <img alt="Vue logo" src="./assets/logo.png" />
    <NewTodoForm msg="Welcome to my todo list" />
</template>

<script>
import NewTodoForm from "./components/NewTodoForm.vue"

export default {
    name: "App",
    components: {
        NewTodoForm,
    },
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
ul {
    list-style: none;
}
</style>
