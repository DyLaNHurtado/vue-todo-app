<template>
  <div id="header">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/95/Vue.js_Logo_2.svg/512px-Vue.js_Logo_2.svg.png?20170919082558" alt=""/>
    <span>Made with 💚 by <a href="https://github.com/DyLaNHurtado" target="_blank"> DyLaNHurtado</a></span> 
  </div>
  <div id="main-container"> 
    <h2>Vue-Todo-App</h2>
    <TodoComponent v-bind:todoList="copyTodos"/>
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
    this.copyTodos =  this.todos;
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
  background: linear-gradient(to bottom, #3d749e, rgba(248, 248, 248, 0.857));
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
  box-shadow: 2px 2px 2px 2px rgb(0, 0, 0);
  padding: 4vw 4vw;
}
#header{
  background: #323232;
  padding: 2vh;
  display:flex;
  align-items: center;
  justify-content: space-evenly;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}

h2{
  padding: 0 10px;
  text-align: center;
}
img{
  position: absolute;
  top: 0.3em;
  left: 0.3em;
  height: 7vh;
}
a{
  color:rgb(255, 191, 88);
  text-decoration: none;
  transition: all;
  transition-duration: 500ms;
}
a:hover{
  color:rgb(144, 185, 255);
  text-decoration: none;
}
</style>
