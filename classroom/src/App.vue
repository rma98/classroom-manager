<template>
  <h1>{{name}}</h1>
  <p v-if="status ==='active'">user active</p>
  <p v-else-if="status ==='pending'"> user pending</p>
  <p v-else>user inactive</p>
  
  <form @submit.prevent="addTask"> 
    <label for="newTask"> add Task</label>
    <input type="text" id = "newTask" name="newTask" v-model="newTask">
    <button type="submmit">submmit</button>
  </form>
  
  <h2>Tasks to be done</h2>
  <ul>
    <li v-for="(task, index) in tasks" :key="task">
      <span>{{ task }}</span>
      <button @click="deleteTask(index)">x</button>
    </li>
  </ul>
  <!-- <a v-bind:href="link">Google search</a> -->
   <a :href="link">Google Search</a>
   <!-- <button v-on:click="toogleStatus">change Status</button> -->
    <br>
   <button @click="toogleStatus">change Status</button>
</template>

<script setup>
import {ref} from 'vue';

const name = ref("Vagner Alves");
const status = ref ('pending');
const tasks =  ref(['task one', 'task two', 'task three']);
const newTask =  ref('')

const toogleStatus = () => {
    if ( status.value === 'active'){
        status.value = 'pending'
      }

    else if (status.value === 'pending'){
        status.value = 'inactive'
      }

    else {
        status.value = 'active'
      }
    };

const addTask = () => {
  if (newTask.value.trim() !== ''){
    tasks.value.push(newTask.value);
    newTask.value = '';
  }
}
</script>
