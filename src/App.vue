<template>
  <Header/>
  <NewTask @AddTask="handlerAddTask"/>
  <Tasks  :tasks="taskList" @DeleteTask="handlerDeleteTask"/>
  <Remove @DeleteAll="handlerDeleteAll" :value="tasksLenght"/>
</template>

<script setup lang="ts">
import Header from './components/Header.vue'
import NewTask from './components/addTask.vue'
import Tasks from './components/Tasks.vue'
import Remove from './components/Remove.vue'


//import functions vue
import { computed, ref } from 'vue'




// lenght computed
const tasksLenght = computed( () => {
  return taskList.value.length
})

// props to Task
const taskList = ref([
  {id: 1, name: "lavar roupa", status: "pendente"},
  {id: 2, name: "limpar casa", status: "pendente"},
  {id: 3, name: "estudar", status: "pendente"},
  {id: 4, name: "passear com o dog", status: "pendente"},
])

// delete all task
const handlerDeleteAll = () => {
  taskList.value = []
}
// delete task
const handlerDeleteTask = (id:number) => {
  taskList.value = taskList.value.filter( (task) => task.id !== id)
}

// generate unique id
const generateID = () => Math.floor(Math.random() * 10000)

// add task
const handlerAddTask = (task:string) => {
  taskList.value.push({id: generateID(), name: task, status: "pendente"})
}
</script>


<style scoped>
</style>  