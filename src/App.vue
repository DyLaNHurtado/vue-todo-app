<template>
<div>
  <div id="header"></div>
  <div id="main-container">
    <h2>Vue-Todo-App</h2>
    <TodoComponent v-bind:todoList="copyTodos"/>
  </div>
</div>
</template>

<script>
import TodoComponent from './components/Todo.vue'


export default {
  name: 'App',
  components: {
    TodoComponent,
  },
  data(){
    return {
      todos:[{
        id:0,
        title: 'Comprar la cena',
        completed: true,
      },
      {
        id:1,
        title: 'Jugar a la Play',
        completed: false,
      },
      {
        id:2,
        title: 'Sacar al perro',
        completed: false,
      }
      ],
      copyTodos: []
    }
  },
  created(){
    this.copyTodos = [... this.todos]
  }
}
</script>

<style>

*{
  box-sizing: border-box;
}
html,body{
  font-family: Arial, Helvetica, sans-serif;
  font-size: 1.5em;
  padding: 0;
  margin: 0;
  background: linear-gradient(to bottom, #537895, rgb(0, 0, 0));
  background-repeat: no-repeat;
  color:white;
  height: 100%;
 
}
#main-container{
  background: linear-gradient(to bottom, #FF5F6D, #FFC371 );
  width: 70vw;
  margin: 100px auto;
  border: 10px solid #f2f2f2;
  border-radius: 50px;
  box-shadow: 1px 1px 2px 2px rgb(0, 0, 0);
  padding: 30px 15px;
}
#header{
  background: #323232;
  padding: 10px;
}

h2{
  padding: 0 10px;
  text-align: center;
}
</style>
