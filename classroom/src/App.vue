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
import {ref} from 'vue';
   export default{
    setup(){
      const name = ref("Vagner Alves");
      const status = ref ('pending');
      const task =  ref(['task one', 'task two', 'task three']);

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
      return{
        name,
        status,
        task,
        toogleStatus,
      }; 
    },
   }
    
</script>
