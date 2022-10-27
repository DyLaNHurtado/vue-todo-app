<template>
  <div id="container-edit">
        <h3>✏️ Edit</h3>
        <div id="input-container">
            <input type="text" id="edit" v-model="dataValue" />
            <button id="ok-button" @click="$emit('closeEdit',dataValue)">Ok</button>
        </div>
  </div>
</template>

<script>
export default {
    name: "EditComponent",
    props: {
        onEdit:{type:Boolean},
        inputValue:{type:String},
    },
    data () {
    return {
        dataValue: this.inputValue
    }},
  emits: ['closeEdit'],

}
</script>

<style scoped>
    #edit{
        padding: 1em;
        margin-bottom: 0.5em;
        margin: 0 1em;
        width: 100%;
    }

    #ok-button{
        padding: 1em;
        width: 15%;
        border: 2px solid transparent;
        margin: 0;
        background-color: #c3c3c3;
        cursor: pointer;
    }
    #ok-button:hover{
        transition: all;
        transition-duration: 400ms;
        border:2px solid rgba(43, 255, 106, 0.623);
        background-color: rgba(13, 14, 12, 0.678);
        color:whitesmoke;
    }

    #container-edit{
        flex-direction: column;
        padding: 0.2em 0;
        overflow: hidden;
        padding: 10px 15px;
        box-shadow: 0px 11px 15px -7px rgba(0, 0, 0, 0.2), 0px 24px 38px 3px rgba(0, 0, 0, 0.14), 0px 9px 46px 8px rgba(0, 0, 0, 0.12);
        background: white;
        color: rgba(0, 0, 0, 0.87);
        border:2px solid white;
        position: absolute;
        width: 60%;
        z-index: 100;
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
