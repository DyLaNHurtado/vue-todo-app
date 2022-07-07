<template>
    <div id="search-container">
        <input type="text" name="search" id="search" placeholder="Enter task to do..."/>
        <button id="add-button">Add</button>
    </div>
</template>

<script>
export default {
  name: 'SearchComponent',
  props: {

  }
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
  transition-duration: 500ms;
  background-color: #00194f;
  color:white;
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
  background: linear-gradient(to bottom ,#ffe520,#ff9501);
  cursor: pointer;
  color:white;
  width: 40%;
  font-size: large;
}

#add-button:hover{
  background: linear-gradient(to bottom ,#69710c,#7e4b04);
    -webkit-transition: background-color 1000ms linear;
    -ms-transition: background-color 1000ms linear;
    transition: background-color 1000ms linear;
}

#add-button:active{
  background: linear-gradient(to bottom ,#f4ff78,#ffac39);
  transition: all;
  transition-duration: 200ms;
}
#search-container{
  width: 100%;
  display: flex;
  flex-direction: row;
  border: 4px solid #424242;
  border-radius: 100px;
}
</style>
