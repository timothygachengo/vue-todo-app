<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "../components/Todos.vue";
import AddTodo from "../components/AddTodo.vue";
import axios from 'axios'
export default {
  name: "Home",
  components: {
    Todos,
    AddTodo,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    addTodo(newTodo){
      this.todos = [...this.todos, newTodo]
    }
  },
  created (){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=20')
    .then(res =>{
      if(res.status === 200){
        const data = res.data;
        this.todos = data
      }
    })
    .catch(err => console.error(err));
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing : border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.btn {
  display: inline-block;
  border : none;
  background : #555;
  color : #fff;
  padding : 7px 20px;
  cursor : pointer;
}

.btn:hover {
  background : #666;
}
</style>
