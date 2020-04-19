<template>
    <div v-bind:class="{ 'is-completed': todo.completed}">
        <input type="checkbox" v-on:change="markComplete">
        <h2>{{todo.title}}</h2>
        <span class="dot" @click="$emit('del-todo', todo.id)"> X </span>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        markComplete(){
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>
    div{
        width: 200px;

    }
    h2, div{
        display: inline;
    }
    /* span{ */
        /* margin-left: 20px; */
        /* background-color: red; */
        /* border-radius: 1.2px; */
    /* } */
    .dot {
        height: 20px;
        width: 25px;
        background-color: #dc3a3a;
        border-radius: 50%;
        display: inline-block;
        cursor: pointer;
        padding-top: 5px;
        margin-left: 20px;
    }
    .is-completed{
        text-decoration: line-through;
    }
</style>