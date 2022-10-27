<template>
  <div id="bg-dark" v-if="islightsOn"></div>
  <div id="main-container"> 
    <h2>Vue-Todo-App</h2>
    <TodoComponent  :todoList="todos" @turnLightsOff="changeDarkBg" @turnLightsOn="changeDarkBg"/>
  </div>
  <a href="https://github.com/DyLaNHurtado" target="_blank">
  <div id="footer">
    <span>Made with 💚 by  DyLaNHurtado</span> 
  </div></a>
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
      islightsOn:false
    }
  },
  methods:{
    changeDarkBg(){
      this.islightsOn = !this.islightsOn;
    }
  },  
}
</script>

<style>

#bg-dark{
  background-color: #222222be;
  position: absolute;
  top: 0;
  left: 0;
  overflow: hidden;
  height: 100vh;
  width: 100vw;
  z-index: 99;
  
}

html{
  font-family: Arial, Helvetica, sans-serif;  
  padding: 0;
  margin: 0;
  background: linear-gradient(to top, #797878, rgba(248, 248, 248, 0.857));
  background-repeat: no-repeat;
  color:white;
  min-height: 100%;
 
}
#main-container{
  background: #f2f2f2;
  width: 70vw;
  margin: 100px auto;
  border: 4px solid #e2e2e2;
  padding: 4vw 4vw;
  height: 100%;
}
#footer{
  background-color: #323232;
  padding: 2vh;
  display:flex;
  align-items: center;
  justify-content: space-evenly;
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  z-index: 5;
}

h2{
  padding: 10px 10px;
  text-align: center;
  font-size: 2em;
  color:rgb(125, 202, 122);
}
a{
  color:whitesmoke;
  text-decoration: none;
  transition: all;
  transition-duration: 500ms;
}
a:hover{
  color:rgb(125, 202, 122);
  text-decoration: none;
}
</style>
