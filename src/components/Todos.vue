<template>
 <div>
    <Header/>
    <ul>
    <div v-for="(todo) in todos" :key="todo.id">
      <TodoItem :todo="todo" v-on:del="$emit('del', todo.id)"/>
    </div>
    </ul>
 </div>
</template>

<script>
import TodoItem from "./TodoItem";
import Header from './layout/Header';

export default {
    name: "Todos",
    components: {
      TodoItem, Header
    },
    props: ["todos"]
}
</script>