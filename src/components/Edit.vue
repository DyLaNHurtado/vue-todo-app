<!-- eslint-disable vue/no-mutating-props -->
<template>
  <div id="container-edit" @open-edit="openEdit(d)">
        <h3>✏️ Edit</h3>
        <div id="input-container">
            <input type="text" id="edit" v-model="editInput" />
            <button id="ok-button" @click="closeEdit(editInput)">Ok</button>
        </div>
  </div>
</template>

<script>
export default {
    name: "EditComponent",
    props: {
        todo: {
        type: Object,
        required: true
        },
        editInput:{
            type: String,
            required: true
        }
    },
  emits: ['closeEdit'],
  setup (props, { emit }) {
    const closeEdit = () => {
            const edit = document.getElementById('edit');
            console.log(edit.value);
            edit.value="";
            console.log(edit.value);
            const dialog = document.getElementById('container-edit');
            dialog.style="display:none"
            emit('closeEdit',edit.value);
        }
        const openEdit = (d) =>{
            const dialog = document.getElementById('container-edit');
            dialog.style="display:flex";
            console.log(d);
        }
    return {closeEdit,openEdit}
}

}
</script>

<style scoped>
    #edit{
        padding: 1em;
        border-radius: 10px;
        font-size: x-large;
        margin-bottom: 0.5em;
        margin: 0 1em;
        width: 100%;
    }
    #edit:focus{
        border:4px solid rgb(246, 171, 95);
    }
    #ok-button{
        font-size: x-large;
        padding: 1em;
        width: 15%;
        border: 4px solid transparent;
        margin: 0;
        border-radius: 100px;
    }
    #ok-button:hover{
        transition: all;
        transition-duration: 400ms;
        border:4px solid rgb(255, 134, 34);
        background-color: rgb(255, 210, 137);
    }
    #ok-button:active{
        border:4px solid rgb(0, 0, 0);
        background-color: rgb(255, 232, 196);
        scale: 1.1;
    }
    #container-edit{
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
