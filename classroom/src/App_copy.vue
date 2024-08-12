<template>
    <h1>{{name}}</h1>
    <p v-if="status ==='active'">user active</p>
    <p v-else-if="status ==='pending'"> user pending</p>
    <p v-else>user inactive</p>
  
    <h2>Tasks to be done</h2>
    <ul>
      <li v-for="tasks in task" :key="task">{{ tasks }}</li>
    </ul>
    <!-- <a v-bind:href="link">Google search</a> -->
     <a :href="link">Google Search</a>
     <!-- <button v-on:click="toogleStatus">change Status</button> -->
      <br>
     <button @click="toogleStatus">change Status</button>
  </template>
  
  <script>
    export default{
      data (){
        return{
          name: "Vagner Alves",
          status: 'pending',
          task: ['task one', 'task two', 'task three'],
          link: 'https://www.google.com'
  
        };
      },
  
      methods: {
        toogleStatus(){
          if (this.status === 'active'){
            this.status = 'pending'
          }
  
          else if (this.status === 'pending'){
            this.status = 'inactive'
          }
  
          else {
            this.status = 'active'
          }
        }
      }
    }  
  </script>

<script>
import {onMounted, ref} from 'vue';

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

const deleteTask = (index) =>{
  tasks.value.splice(index,1);
}

onMounted( async () =>{
  try{
    const response = await fetch('https://jsonplaceholder.typicode.com/todos');
    const data =  await response.json();
    tasks.value = data.map((tasks) => tasks.title);

  }
  catch(error){
    console.log('error fetching the data.');
  }
});
</script>