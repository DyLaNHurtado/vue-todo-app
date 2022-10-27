<template>
  <div class="container">       
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
  methods:{
    completeTask(task){
            task.isChecked = !task.isChecked
            task.completed= !task.completed;
        },
    deleteTask(todoList,task){
        const index = todoList.indexOf(task);
        if(index!=-1){
            todoList.splice(index,1);
        }
    },
    editTask(todoList,task){
        this.$emit('openEditTask',task.title,todoList.indexOf(task));
    }
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
        border-bottom:1px solid #d6d6d6;
        padding: 0.3em 0;
        position: relative;
        z-index: 2;
        -webkit-transition: all .1s;
        -moz-transition: all .1s;
        transition: all .1s;
    }
    .container:hover{
        z-index: 3;
        background-color: white;
        -webkit-box-shadow: 0 0 14px rgba(34, 44, 55, 0.25);
        -moz-box-shadow: 0 0 14px rgba(34, 44, 55, 0.25);
        box-shadow: 0 0 14px rgba(34, 44, 55, 0.25);
    }
    .todo-actions{
        display: flex;
        flex-direction: row;
    }
    
    .todo-body{
        width: 100%;
        border-radius: 10px;
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
        background: #db756d;
        border: 2px solid #c2c2c2;
        cursor: pointer;
        transition-duration: 200ms;
    }
    #delete-button:hover{
        background: #333333;
        color: rgb(255, 135, 135);
        fill:rgb(255, 135, 135);
        border: 2px solid #f35
    }

    #delete-button:active{
        transition-duration: 100ms;
        scale: 1.1;
        background-color: #a5a5a5;
    }
    #edit-button{
        background: #65b88c;
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
