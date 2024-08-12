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
