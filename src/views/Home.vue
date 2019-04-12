<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import axios from 'axios';
import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo';


export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo
  },

  data () { 
    return {
      todos : [],
    }
  }, 

  methods : { 
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res =>  this.todos = this.todos.filter(todo => todo.id !== id))
        .catch(err => console.log(err));
      

    },

    addTodo(todo) {
      const {title , completed } = todo;
      axios.post('https://jsonplaceholder.typicode.com/todos' , {
        title,
        completed
      })
        .then(res => this.todos.push(res.data) )
      
        .catch(err => console.log(err));

    },
  },

  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err))
  }
}
</script>

<style>
/* there we put our global styles */
  * {
    box-sizing: border-box;
    padding: 0;
    margin: 0;
  }

  body { 
    font-size: inherit;
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }

  .btn { 
    display: inline-block;
    border: none;
    background: #555 ;
    color: #fff; 
    padding: 7px 20px ; 
    cursor: pointer;
  }

  .btn:hover {
    background: #666;
  }
</style>
