<template>
  <div class="container" v-on:close-edit="(d)=>alert(d)">       
    <div class="todo-body checkbox" @click="completeTask(todo)" v-bind:class="{completed:todo.completed}" v-bind:checked="todo.completed">
        <input type="checkbox" name="check" v-bind:checked="todo.completed" id="checkbox">
        <span>{{todo.title}}</span>
    </div>
    <div class="todo-actions">
        <button id="edit-button" @click="editTask(todoList,todo)">Editar</button>
        <button id="delete-button" @click="deleteTask(todoList,todo)">Eliminar</button>
    </div>
  </div>
</template>

<script>
export default {
    name: 'TaskComponent',
    props: {
        todo: {
        type: Object,
        required: true
        },
        todoList:{
            type: [],
            required: true
        }
    },
  emits: ['openEditTask'],
  setup (props, { emit }) {
    const completeTask = (task) => {
            task.isChecked = !task.isChecked
            task.completed= !task.completed;
        }
    const deleteTask = (todoList,task) => {
        const index = todoList.indexOf(task);
        if(index!=-1){
            todoList.splice(index,1);
        }
    }
    const editTask = (todoList,task) => {
        emit('openEditTask',todoList.indexOf(task));
    }
    return {completeTask,deleteTask,editTask}
}

}
</script>

<style scoped>
     .completed{
        background-color: #cdcdcd;
        color:#999;
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
        padding: 0.5em 0.5em;
    }
    .todo-body:not(.completed){
        background-color: white;
        color:#333;
        font-weight: bolder;
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
    span{
        user-select: none;
    }

</style>
