<script setup>
 import Navbar from '@/components/NavBar.vue';
 import Hero from '@/components/Hero.vue';
 import Homecards from '@/components/Homecards.vue';
 import JobListings  from './components/JobListings.vue';
</script>


<template>
  <Navbar/>
  <Hero title="IFPE - Palmares" subtitle="veja as salas disponiveis abaixo"/>
  <Homecards/>
  <JobListings :limit="3" :show-button="true"/>

</template>