<template>
    <EditComponent v-bind:todo="todo" :editStatus="false" @closeEdit="close()"/>
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
    props: {
        todoList: [],
        editStatus: Boolean,
    },
    emits:['openEdit'],
    components: { TaskComponent,SearchComponent,EditComponent },
    setup(){
        const close = (param)=>{
            console.log(param);
        }
        const open = (param)=>{
            console.log("dasd",param);
        }
        return {close, open}
    }
}
</script>

<style scoped>
    .bar{
        width: 100%;
        padding: 2px;
        display: flex;
        flex-direction: row;
    }
</style>
