<template>
    <EditComponent v-if="onEdit" :inputValue="inputValue" @closeEdit="close"/>
    <div class="container"  @keydown.esc="cancel">
        <div class="bar">
            <SearchComponent :todoList="todoList"/>
        </div>
    <div :key="todo.id" v-for="todo in todoList">
        <TaskComponent :todo="todo" :onEdit="onEdit" @openEditTask="this.open" :todoList="todoList"/>
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
        todoList: Array,
    },
    data(){
        return{onEdit:false,inputValue:"",index:0,editTodoList:this.todoList}
    },
    emits:['openEdit'],
    components: { TaskComponent,SearchComponent,EditComponent },
    methods:{
        cancel(){
            this.onEdit= false;
            this.$emit('turnLightsOn');
        },
        close(newTitle){
            this.editTodoList[this.index].title=newTitle;
            this.onEdit= false;
            this.$emit('turnLightsOn');
        },
        open(title,index){
            this.index=index;
            this.onEdit = true;
            this.$emit('turnLightsOff');
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
