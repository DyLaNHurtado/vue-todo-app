<template>
    <EditComponent v-if="onEdit" :inputValue="inputValue" @closeEdit="close"/>
    <div class="container">
        <div class="bar">
            <SearchComponent v-bind:todoList="todoList"/>
        </div>
    <div v-bind:key="todo.id" v-for="todo in todoList">
        <TaskComponent v-bind:todo="todo" @openEditTask="this.open"  v-bind:todoList="todoList"/>
    </div>
  </div>
</template>

<script>
import TaskComponent from './Task.vue';
import SearchComponent from './Search.vue'
import EditComponent from './Edit.vue'
export default {
    name: "TodoComponent",
    
    props: {
        todoList: [],
    },
    data(){
        return{onEdit:false,inputValue:"",index:0,editTodoList:this.todoList}
    },
    emits:['openEdit'],
    components: { TaskComponent,SearchComponent,EditComponent },
    methods:{
        close(newTitle){
            this.editTodoList[this.index].title=newTitle;
            this.onEdit= false;
        },
        open(title,index){
            this.index=index;
            this.onEdit = true;
            this.inputValue = title;
        }
    }       
}
</script>

<style scoped>
    .bar{
        width: 100%;
        display: flex;
        flex-direction: row;
        border-bottom: 2px solid #c2c2c2;
    }
</style>
