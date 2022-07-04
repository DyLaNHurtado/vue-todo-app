<template>
  <div class="container">
    <div class="todo-body" v-bind:class="{completed:todo.completed}">
        <input type="checkbox" v-bind:checked="todo.completed ? 'checked' : ''">
        {{todo.title}}
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
.todo{
        border-bottom: solid 1px #ccc;
        padding: 10px;
    }

    .todo:not(.completed):hover{
        background-color:#424242 ;
    }

    .completed{
        color: #ccc;
        text-decoration: line-through;
    }

    .completed .todo-body{
        text-decoration: line-through;
    }
    .container{
        display: flex;
        flex-direction: row;
        padding: 0.2em 0;
        overflow: hidden;
        padding: 3px 15px;
    }

    .todo-actions{
        display: flex;
        flex-direction: row;
    }
    .todo-body{
        width: 85%;
    }

    button{
        margin: 0 2px;
    }
    
    #delete-button{
        padding: 8px 12px;
        background-color: #f35;
        color: whitesmoke;
        border-radius: 500px;
        border: 2px solid #fff;
        cursor: pointer;

        transition-duration: 700ms;
    }
    #delete-button:hover{
        background-color: #333333;
        color: rgb(255, 135, 135);
        border: 2px solid #f35
    }

    #delete-button:active{
        transition-duration: 100ms;
        scale: 1.1;
        background-color: #dfdfdf;
    }
    #edit-button{
        padding: 8px 12px;
        background-color: rgb(44, 181, 99);
        color: whitesmoke;
        border-radius: 500px;
        border: 2px solid #fff;
        cursor: pointer;

        transition-duration: 700ms;
    }
    #edit-button:hover{
        background-color: #333333;
        color: rgb(135, 255, 197);
        border: 2px solid rgb(44, 181, 99);
    }

    #edit-button:active{
        transition-duration: 100ms;
        scale: 1.1;
        background-color: #dfdfdf;
    }



</style>
