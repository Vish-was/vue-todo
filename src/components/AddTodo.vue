<template>
  <div>
    <form @submit="addTodo">
      <input type="text" v-model="title" name="title" id="title">
      <input type="submit" value="submit">
    </form>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';
export default {
  name: "AddTodo",
  data(){
    return {
      title: 'Add Todo Here ..'
    }
  },
  methods: {
    addTodo(e){
      e.preventDefault();
      const newTodo = {
        id: uuidv4(),
        title: this.title
      }
      this.$emit('add-todo', newTodo);
      this.title = '';
    }
  }
}
</script>
