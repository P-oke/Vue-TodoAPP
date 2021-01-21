<template>
  <div id="app">
    <h2>TodoList</h2>
    <Addtodo v-on:add-todo="addTodo" />
    <Todos :todos="todos" v-on:del-todo="Deletetodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos.vue";
import Addtodo from "./components/Addtodo.vue";

export default {
  name: "App",

  components: {
    Todos,
    Addtodo,
  },

  data() {
    return {
      todos: [],
    };
  },

  methods: {
    Deletetodo(id) {
      const fetchdata = {
        method: "DELETE",
        body: JSON.stringify(id),
        headers: { "content-type": "application/json" },
      };
      fetch(`https://jsonplaceholder.typicode.com/todos/${id}`, fetchdata)
        .then(() => (this.todos = this.todos.filter((todo) => todo.id !== id)))
        .catch((err) => console.log(err.message));
    },

    addTodo(newtodo) {
      const fetchdata = {
        method: "POST",
        body: JSON.stringify(newtodo),
        headers: { "content-type": "application/json" },
      };
      fetch("https://jsonplaceholder.typicode.com/todos", fetchdata)
        .then((res) => res.json())
        .then((jsondata) => (this.todos = [...this.todos, jsondata]))
        .catch((err) => console.log(err.message));
    },
  },

  created() {
    fetch("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then((res) => res.json())
      .then((jsondata) => (this.todos = jsondata))
      .catch((err) => console.log(err.message));
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#app {
  font-family: Arial, Helvetica, sans-serif;
}
h2 {
  text-align: center;
  padding: 10px;
  background-color: #1066c9;
  color: #fff;
}

.btn {
  background-color: #698ef5;
  outline: none;
  color: #fff;
  padding: 8px;
  cursor: pointer;
  border: none;
  font-weight: bold;
}

.btn:hover {
  background-color: #0d77f0;
}
</style>
