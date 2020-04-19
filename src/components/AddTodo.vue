<template>
    <div>
        <form @submit="addTodo">
            <label for="title"> Title</label>
            <input type="text" v-model="title" name="title" placeholder="Title">
            <input type="submit" value="Add Todo" class="btn">
        </form>
    </div>    
</template>

<script>
// import {v4 as uuid} from "uuid";

export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            const newTodo = {
                // id: uuid,
                title: this.title,
                completed: false
            }
            this.$emit("add-Todo", newTodo);
            this.title = '';
        }
    }
}
</script>

<style scoped>
    form{
        margin: 5px;
        flex: content;
    }
    .btn{
        background-color:#484444;
        color: white;
    }

</style>