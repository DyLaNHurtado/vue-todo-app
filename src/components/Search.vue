<template>
    <div id="search-container">
        <input type="text" name="search" id="search" v-model="inputSearch" placeholder="Enter task to do..."/>
        <button id="add-button" @click="addTodo(this.$props.todoList,inputSearch)"><AddIcon/></button>
    </div>
</template>

<script>
import AddIcon from '@/assets/icons/AddIcon.vue';
export default {
  data() {
    return {
      inputSearch:"",
    }
  },
  name: 'SearchComponent',
  components: {
        AddIcon,
  },
  props: {
    todoList: Array,
  },
  methods:{
    addTodo:(todoList,inputSearch) => {
      if(inputSearch.trim()!='' ){
        todoList.push({id:todoList.length,title:inputSearch,completed:false });
        const search = document.getElementById('search');
        search.value='';
      }else{
        alert(' ⛔ Error : Empty name invalid  ⛔ ')
      }
    }
  },
}
</script>

<style scoped>
#search{
  padding: 1em 1em;
  border: 0;
  width: 100%;
}

#search:focus{
  transition: all;
  transition-duration: 900ms;
  transition-delay: 0ms;
  background-color: rgb(225, 250, 227);
  border: 0;
  outline: none;
}

#add-button{
  border:0;
  padding: 1.5em 3em;
  font-weight: bold;
  background: #b9b9b9;
  cursor: pointer;
  color:white;
  fill: rgb(29, 29, 29);
  transition: all;
  transition-duration: 1000ms;
}

#add-button:hover{
  background-color: #333333;
  fill: rgb(67, 184, 104);
  transition: all;
  transition-duration: 500ms;
}

#add-button:active{
  background: linear-gradient(to bottom ,#4f5263,#827e8c);
  transition: all;
  transition-duration: 200ms;
  scale: 1.1;
  border:0;
}
#search-container{
  width: 100%;
  display: flex;
  flex-direction: row;
}
</style>
