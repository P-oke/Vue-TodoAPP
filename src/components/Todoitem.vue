<template>
<div class="todo-item" :class="{'is-complete':todo.completed}">
    <p>
        <input type="checkbox" name="" id="" v-on:change="Checkcomplete">
        {{todo.title}}
        <button class="del" @click="$emit('del-todo', todo.id)">X</button>
    </p>
    
</div>
  
</template>

<script>
export default {
  name:"Todoitem",
  props:["todo"],

  methods:{
      Checkcomplete(){
        this.todo.completed =! this.todo.completed
      }

  }
}



</script>

<style>
.todo-item {
    background: #e6ebf5;
    padding: 10px;
    border-bottom: 1px #c2c2c2 solid;
    
  }
  .is-complete {
    text-decoration: line-through;
  }
  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>