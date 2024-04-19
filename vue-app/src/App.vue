<script setup>

import Task from "./components/Task.vue"

import {ref} from 'vue'

const ToDo = ref ([])
const textInput = ref ("")

const addToDo = ()=>{
  const value = textInput.value

  if (value.length < 3){
    alert("Text should have atleast 3 character")
    return
  }
  ToDo.value.push(value)
  textInput.value=""
}

const onDelete = (index) =>{
  ToDo.value.splice(index, 1)
}
</script>

<template>
  <main>

    <h1>My To-Do App</h1>
    <div class="input">
      <input  v-model="textInput"  placeholder="Enter To-Do"/>
      <button @click="addToDo">Add To-Do </button>
    </div>

    <div class="task">

      <Task v-for="task in ToDo " :key="index" :name="task" :index="index" @onDelete="onDelete" />
      

    </div>
    
  </main>
</template>

<style scoped>


main{
  background-color: white;
  border-radius:24px ;
  width: 100%;
  min-width: 400px;
  color: gray;
  margin-top: 80px;
  padding: 20px;
}

h1{
  text-align: center;
}
.input{
  display: flex;
  
  margin: 20px 0px;
}
.input button{
  flex-basis: 30%;
  height: 44px;
}

input{
  height: 44px;
  flex-basis: 70%;

}



</style>