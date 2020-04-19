<template>
  <div id="home">
    <AddTodo v-on:add-Todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from '../components/Todos.vue'
import AddTodo from '../components/AddTodo.vue'
import axios from 'axios'


export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo
  },
  data(){
    return {
      todos:[]

    }

  },
  methods: {
    deleteTodo(id){
      console.log(id, 'delete this');
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`). 
      then(this.todos = this.todos.filter(todo  => todo.id !== id )). catch(err => console.log(err));
      
    },
    addTodo(newTodo){
      const {title, completed} = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos', {title, completed}). 
      then(res => this.todos = [...this.todos, res.data]). catch(err => console.log(err));
    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5').
    then(response => this.todos=response.data).
    catch(err => console.log(err))
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
