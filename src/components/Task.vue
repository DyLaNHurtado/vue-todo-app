<template>
  <div class="container">       
    <div class="todo-body" v-bind:class="{completed:todo.completed}">
         <input type="checkbox" id="checkbox" v-bind:checked="todo.completed? 'checked':''">
        <span>{{todo.title}}</span>
    </div>
    <div class="todo-actions">
        <button id="edit-button">Editar</button>
        <button id="delete-button">Eliminar</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TaskComponent',
  props: ['todo']
}
</script>

<style scoped>
     .completed{
        background-color: #3ed461;
        text-decoration: line-through;
        border: 3px solid #414141;
    }
    .container{
        display: flex;
        flex-direction: row;
        padding: 0.2em 0;
        overflow: hidden;
        padding: 10px 15px;
        flood-opacity: 30%;
        border-radius: 10px;
        background-color: #333;
        border:2px solid white;
        margin: 0.3em 0;
        
    }

    .todo-actions{
        display: flex;
        flex-direction: row;
    }
    
    .todo-body{
        width: 100%;
        border-radius: 10px;
        margin-right: 20px;
        box-sizing: border-box;
        padding: 5px;
    }
    .todo-body:not(.completed){
        background-color: #ff8248;
        border: 3px solid #414141;
    }

    button{
        margin: 0 2px;
        font-size: xx-large;
    }
    
    #delete-button{
        padding: 0.2em 0.75em;
        background: linear-gradient(to bottom, #FF512F , #DD2476);
        color: whitesmoke;
        border-radius: 500px;
        border: 2px solid #fff;
        cursor: pointer;
        transition-duration: 200ms;
    }
    #delete-button:hover{
        background: #333333;
        color: rgb(255, 135, 135);
        border: 2px solid #f35
    }

    #delete-button:active{
        transition-duration: 100ms;
        scale: 1.1;
        background-color: #a5a5a5;
    }
    #edit-button{
        padding: 0.2em 0.75em;
        background: linear-gradient(to bottom ,#FCEE21,#009245);
        color: whitesmoke;
        border-radius: 500px;
        border: 2px solid #fff;
        cursor: pointer;
        transition-duration: 200ms;
    }
    #edit-button:hover{
        background: #333333;
        color: rgb(135, 255, 197);
        border: 2px solid rgb(44, 181, 99);
    }

    #edit-button:active{
        transition-duration: 100ms;
        scale: 1.1;
        background-color: #a5a5a5;
    }
    #checkbox{
        margin: 2% 3%;
        scale: 2;
        margin-bottom: 3%;
    }
</style>
