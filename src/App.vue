<template>
  <div id="app">
    <Todos v-bind:todos="todos" v-on:del="deleteTodo" v-on:addTodo="addTodo"/>
    <AddTodo v-on:add-todo="addTodo"/>
  </div>
</template>

<script>
import Todos from './components/Todos.vue'
import AddTodo from './components/AddTodo';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Todos, AddTodo
  }, 
  data(){
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id != id);
    },
    addTodo(newTodo){
      this.todos = [...this.todos, newTodo]
    },
    created(){
      axios.get('https://jsonplaceholder.typicode.com/todos').then(res => this.todos = res.data);
    }
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
  margin-top: 60px;
}
</style>
