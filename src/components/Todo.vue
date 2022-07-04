<template>
  <div class="container">
    Todo
    <div class="bar">
        <SearchComponent/>
        <AddComponent/>
    </div>
    <div v-bind:key="todo.id" v-for="todo in todoList">
        <TaskComponent v-bind:todo="todo" />
    </div>
  </div>
</template>

<script>
import TaskComponent from './Task.vue';
import AddComponent from './Add.vue'
import SearchComponent from './Search.vue'
export default {
    name: "TodoComponent",
    props: {
        todoList: []
    },
    components: { TaskComponent,SearchComponent,AddComponent }
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
