<template>
  <div>

  <div v-bind:key="todo.id" v-for="todo in todos">
    <Todoitem :todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/>
  </div>
  
</div>

</template>

<script>
import Todoitem from "./Todoitem"

export default {
  components: { Todoitem },
  name:"Todos",

  componenets:{
    Todoitem
  },

  props:["todos"]

}

</script>

<style>

</style>