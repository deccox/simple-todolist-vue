<template>
    <div id="boardTask">
        <div class="itemTask" v-for="task in props.tasks" v-bind:key="task.id">
            <div>
                <span class="name-task">{{task.name}}</span>
            </div>
            <div>
                <span 
                    v-bind:class="task.status" class="itemhover"
                    @click="handlerChangeStatus(task)">
                {{task.status}}
                </span> > 
                <span class="task-settings" @click="handlerDeleteTask(task.id)">X</span>
            </div>
        </div>
        
        
    </div>
</template>


<script setup lang="ts">
type TaskType = { id: number, name: string, status: string}
const props = defineProps<{
    tasks: TaskType[]
}>();

// define um evento, onde, vai enviar ap App view e deletar do array a task
const emit = defineEmits(['DeleteTask'])


// click que deleta uma task
const handlerDeleteTask = (data:number) => {
    emit('DeleteTask', data)
}

// click que muda o status da tarefa
const handlerChangeStatus = (task: {id: number, name: string, status: string}) => {
    const status:Array<string> = ["pendente","concluida","progresso"] 
    const aux: number = status.indexOf(task.status)
    task.status = aux == 2 ? status[0] : aux == 0 ? status[1] : status[2] 
}
</script>







<style scoped>

#boardTask{
    display: flex;
    justify-content: center;
    align-content: center;
    flex-direction: column;
    width: 100%;
    gap: 10px;
    font-family: Calibri;
}

.itemTask{
    display: flex;
    justify-content: space-between;
    
    
}

.name-task, .task-status, .task-settings{
    font-size: 1em;
    font-weight: lighter;
    font-family: Calibri;
}

.pendente{
    background-color: rgb(255, 132, 132);
    padding: 2px;
    border-radius: 5px;
    font-size: 0.9em;
    font-weight: lighter;
    font-family: Calibri;
    cursor: pointer;
    user-select: none;
}

.concluida{
    background-color: rgb(130, 255, 130);
    padding: 2px;
    border-radius: 5px;
    font-size: 0.9em;
    font-weight: lighter;
    font-family: Calibri;
    cursor: pointer;
    user-select: none;
}

.progresso{
    background-color: rgb(255, 205, 112);
    padding: 2px;
    border-radius: 5px;
    font-size: 0.9em;
    font-weight: lighter;
    font-family: Calibri;
    cursor: pointer;
    user-select: none;
}

.task-settings{
    cursor: pointer;
    user-select: none;
}
.itemhover:hover{
    opacity: 0.6;
}

</style>