<template>
    <div class="">
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
  padding: 1.5em 1em;
  border-radius: 100px;
  border-bottom-right-radius: 0px;
  border-top-right-radius: 0px;
  border:0;
}
#add-button{
  border:0;
  padding: 1.5em 2em;
  font-weight: bold;
  border-radius: 100px;
  border-bottom-left-radius: 0px;
  border-top-left-radius: 0px;
  background: linear-gradient(to right ,#FCEE21,#009245  );
}
</style>
