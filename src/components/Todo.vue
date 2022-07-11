<template>
    <EditComponent v-bind:todo="todo"/>
    <div class="container">
        <div class="bar">
            <SearchComponent v-bind:todoList="todoList"/>
        </div>
    <div v-bind:key="todo.id" v-for="todo in todoList">
        <TaskComponent v-bind:todo="todo" v-bind:todoList="todoList" />
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
        todoList: []
    },
    components: { TaskComponent,SearchComponent,EditComponent } 
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
