<template>
    <div id="footer">
        <button id="btn-delete" v-if="props.value"
            @click="handlerDeleteAll"    
        >Remove Tasks</button>
    </div>
</template>


<script setup lang="ts">
const emit = defineEmits(['DeleteAll'])

const props = defineProps<{
    value: number
}>()

const handlerDeleteAll = () => {

    emit('DeleteAll')

}

</script>



<style scoped>


#footer{
    margin-top: 30px;
    display: flex;
    width: 100%;
    justify-content: end;
}
#btn-delete{
    background-color: rgb(255, 205, 205);
    font-size: 1.2rem;
    font-weight: bolder;
    color: rgba(0, 0, 0, 0.318);
    border: none;
    padding: 10px;
    border-radius: 5px;
    
}
</style>