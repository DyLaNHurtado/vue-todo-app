<template>
  <div class="container">
        <h3>✏️ Edit</h3>
        <div id="input-container">
            <input type="text" class="edit" />
            <button id="ok-button">Ok</button>
        </div>
        
  </div>
</template>

<script>
export default {
    name: "EditComponent",
    props: ['todo'],
    methods:{}
}
</script>

<style scoped>
    .edit{
        padding: 1em;
        border-radius: 10px;
        font-size: x-large;
        margin-bottom: 0.5em;
        margin: 0 1em;
        width: 100%;
    }
    .edit:focus{
        border:4px solid rgb(246, 171, 95);
    }
    #ok-button{
        font-size: x-large;
        padding: 1em;
        width: 15%;
        border: 4px solid transparent;
        margin: 0;
        border-radius: 100px;
        border:0;
    }
    #ok-button:hover{
        border:4px solid greenyellow;
        background-color: black;

    }
    .container{
        display: flex;
        flex-direction: column;
        padding: 0.2em 0;
        overflow: hidden;
        padding: 10px 15px;
        flood-opacity: 30%;
        border-radius: 10px;
        background-color: #333;
        border:2px solid white;
        position: absolute;
        width: 60%;
        z-index: 100;
        box-shadow: 2px 2px 1px 1px black;
    }
    #input-container{
        display:flex;
        flex-direction: row;
        justify-content: center;
        padding-bottom: 4vw;
    }
    h3{
        width: 100%;
        text-align: center;
    }
</style>
