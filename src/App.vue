<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <!-- 1. bind the state and pass on to the child component -->
    <!-- 2. v-on: is receiving the event del-todo from child component and call a function deleteTodo -->
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/> 
  </div>
</template>

<script>

import Header from './components/layout/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';
// import axios from 'axios';

export default {
  name: 'App',
  components: {
    Todos,
    Header,
    AddTodo      
  },
  data() {   //this is the state
    return {
      todos: []     // to pass the todos to <Todos /> use v-bind, call it :todos and pass 
      //         [        
      //   {          // on the todos array as "todos"
      //     id: 1, 
      //     title: "Todo One",
      //     completed: false
      //   },
      //           {
      //     id: 2, 
      //     title: "Todo Two",
      //     completed: false
      //   },
      //           {
      //     id: 3, 
      //     title: "Todo Three",
      //     completed: false
      //   }

      // ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      // const { title, completed } = newTodo;
    
      // axios.post('https://jsonplaceholder.typicode.com/todos', {
      //   title,     //same as title: title
      //   completed
      // })
      // .then(res => this.todos = [...this.todos, res.data])
      // .catch(err => console.log(err))

      this.todos = [...this.todos, newTodo]
    }
  },
  // created() {   //like useEffect
  //   axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
  //     .then(res => this.todos = res.data) //filling this.todos with the response
  //     .catch(err => console.log(err))
  // }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
