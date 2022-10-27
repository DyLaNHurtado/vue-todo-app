<template>
    <EditComponent v-if="onEdit" :inputValue="inputValue" @closeEdit="close"/>
    <div class="container">
        <div class="bar">
            <SearchComponent v-bind:todoList="todoList"/>
        </div>
    <div v-bind:key="todo.id" v-for="todo in todoList">
        <TaskComponent v-bind:todo="todo" @openEditTask="open(todo.title)"  v-bind:todoList="todoList"/>
    </div>
  </div>
</template>

<script>
import TaskComponent from './Task.vue';
import SearchComponent from './Search.vue'
import EditComponent from './Edit.vue'
export default {
    name: "TodoComponent",
    data(){
        return{onEdit:false,inputValue:""}
    },
    props: {
        todoList: [],
    },
    emits:['openEdit'],
    components: { TaskComponent,SearchComponent,EditComponent },
    methods:{
        close(dataValue){
            console.log(dataValue);
            this.onEdit= false;
        },
        open(param){
            this.onEdit = true;
            console.log(param+"holaaa");
            this.inputValue = param;
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
