<script setup>
import Calculation from '@/components/Calculation.vue';
</script>

<template>
   <div class="container max-w-screen-lg bg-slate-800 text-white mx-auto p-6 rounded-lg mt-10">
      <h1 class="text-5xl mb-10">Percentage Calculator</h1>
      <div class="mb-20"></div>

      <Calculation operation="percent_of" />
      <div class="mb-10"></div>

      <Calculation operation="is_what_percent" />
      <div class="mb-10"></div>

      <Calculation operation="from_to" />
   </div>
</template>