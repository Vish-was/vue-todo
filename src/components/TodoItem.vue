<template>
  <div class="todo-item">
    <p v-on:click="markComplete" :class="{'flag':todo.flag}">Hey {{todo.title}}
      <button @click="$emit('del', todo.id)">X</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete(){
      this.todo.flag = !this.todo.flag 
      console.log(this.todo.flag)
    }
  }
}
</script>

<style scoped>
.flag {
  text-decoration: line-through;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>