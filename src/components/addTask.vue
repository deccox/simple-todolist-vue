<template>
    <div id="form-board">
        <form action="" @submit.prevent="onSubmit" id="form">
            <input type="text" name="text" v-model="text"  id="text" placeholder="task" >
            <button id="submitbtn">+</button>
        </form>
    </div>
</template>



<script setup lang="ts">
import { defineModel } from 'vue'

// definido evento para adicionar valores no array (app view)
const emit = defineEmits(["AddTask"])



// linkadao com os valores do form
const text = defineModel('text')


const onSubmit = () => {
    emit('AddTask', text.value)
    text.value = ''
}   
</script>


<style scoped>

#form-board{
    width:100%;
    display: flex;
    justify-content: center;
}
#text{
    max-width: 400px;
    width: 100%;
    height: 30px;
    padding: 5px;
    border: 1px solid rgb(149, 211, 240);
    border-radius: 5px;

}

#text:focus{
    outline: none;
}

#submitbtn{
    height: 30px;
    width: 30px;
    display: flex;
    justify-content: center;
    align-items: center;
    border: none;
    background-color: rgb(158, 224, 255);
    border-radius: 5px;
}

#form{
    display: flex;
    flex-direction: row;
    gap: 5px;
    width: 100%;
}


</style>