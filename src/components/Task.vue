<template>
  <div class="container" v-on:close-edit="(d)=>alert(d)">       
    <div class="todo-body checkbox" @click="completeTask(todo)" v-bind:class="{completed:todo.completed}" v-bind:checked="todo.completed">
        <input type="checkbox" name="check" v-bind:checked="todo.completed" id="checkbox">
        <span>{{todo.title}}</span>
    </div>
    <div class="todo-actions">
        <button id="edit-button" @click="editTask(todoList,todo)"><EditIcon/>Edit</button>
        <button id="delete-button" @click="deleteTask(todoList,todo)"><DeleteIcon/>Delete</button>
    </div>
  </div>
</template>

<script>
import EditIcon from '../assets/icons/EditIcon.vue';
import DeleteIcon from '../assets/icons/DeleteIcon.vue';
export default {
    name: 'TaskComponent',
    components: {
        DeleteIcon,EditIcon
  },
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
        color:#999;
        text-decoration: line-through;
    }
    .container{
        display: flex;
        flex-direction: row;
        overflow: hidden;
        padding-left: 0.5em;
        flood-opacity: 30%;
        border-bottom:2px solid #c2c2c2;
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
        cursor: pointer;
    }
    .todo-body:not(.completed){
        color:#333;
        font-weight: bolder;
    }

    button{
        margin: 0 2px;
        font-size: 1em;
        padding: 10px 30px;
        color: whitesmoke;
        fill: whitesmoke;

    }
    
    #delete-button{
        background: linear-gradient(to bottom, #f06246 , #d14584);
        border: 2px solid #c2c2c2;
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
        background: linear-gradient(to bottom ,#f5e941,#188d4f);
        border: 2px solid #c2c2c2;
        cursor: pointer;
        transition-duration: 200ms;
    }
    #edit-button:hover{
        background: #333333;
        color: rgb(135, 255, 197);
        fill:rgb(135, 255, 197);
        border: 2px solid rgb(44, 181, 99);
    }

    #edit-button:active{
        transition-duration: 100ms;
        scale: 1.1;
        background-color: #a5a5a5;
    }
    #checkbox{
        margin: 2% 3%;
        scale: 1.5;
        margin-bottom: 3%;
    }
    span{
        user-select: none;
    }

</style>
