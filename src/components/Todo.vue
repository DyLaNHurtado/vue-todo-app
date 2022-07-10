<template>
  <div class="container">
    <div class="bar">
        <SearchComponent/>
    </div>
    <div v-bind:key="todo.id" v-for="todo in todoList">
        <TaskComponent v-bind:todo="todo" />
    </div>
  </div>
</template>

<script>
import TaskComponent from './Task.vue';
import SearchComponent from './Search.vue'
export default {
    name: "TodoComponent",
    props: {
        todoList: []
    },
    components: { TaskComponent,SearchComponent }
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
