<template>
    <div id="search-container">
        <input type="text" name="search" id="search" v-model="inputSearch" placeholder="Enter task to do..."/>
        <button id="add-button" @click="addTodo(this.$props.todoList,inputSearch)">Add</button>
    </div>
</template>

<script>
export default {
  data() {
    return {
      inputSearch:"",
    }
  },
  name: 'SearchComponent',
  props: {
    todoList: [],
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
  padding: 1.5em 2em;
  border-radius: 100px;
  border-bottom-right-radius: 0px;
  border-top-right-radius: 0px;
  border:0;
  width: 90%;
  font-size: large;
}

#search:focus{
  transition: all;
  transition-duration: 900ms;
  transition-delay: 0ms;
  background-color: #fff4af;
  border: 0;
  outline: none;
}

#add-button{
  border:0;
  padding: 2em 1.5em ;
  font-weight: bold;
  border-radius: 100px;
  border-bottom-left-radius: 0px;
  border-top-left-radius: 0px;
  border-left: 5px solid #424242;
  background: linear-gradient(to bottom ,#ffe520,#ff5a01);
  cursor: pointer;
  color:white;
  width: 40%;
  font-size: large;
  transition: all;
  transition-duration: 1300ms;
}

#add-button:hover{
  background: linear-gradient(to bottom ,#030a31,#564b6e);
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
  border: 4px solid #424242;
  border-radius: 100px;
}
</style>
