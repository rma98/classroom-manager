<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
      <!-- Go Back -->
      <section>
      <div class="container m-auto py-6 px-6">
        <RouterLink
          to="/jobs"
          class="text-green-500 hover:text-green-600 flex items-center"
        >
          <i class="pi pi-arrow-circle-left mr-4"></i> Voltar para as salas.
        </RouterLink>
      </div>
    </section>

</template>