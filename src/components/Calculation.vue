<script setup>
import { ref, computed } from 'vue';

const props = defineProps({
   operation: {
      type: String,
      required: true
   }
});

const txt1 = ref('');
const txt2 = ref('');

if (props.operation === 'percent_of') {
   txt1.value = 'What is';
   txt2.value = '% of';
}
else if (props.operation === 'is_what_percent') {
   txt1.value = '';
   txt2.value = 'is what % of';
}
else if (props.operation === 'from_to') {
   txt1.value = 'Percentage increase / decrease from';
   txt2.value = 'to';
}

const num1 = ref('');
const num2 = ref('');
const answer = computed(() => {
   const n1 = parseInt(num1.value);
   const n2 = parseInt(num2.value);

   let res;

   if (isNaN(n1) || isNaN(n2)) {return '';}
   else if (props.operation === 'percent_of') {res = n2 / n1;}
   else if (props.operation === 'is_what_percent') {res = n1 / n2 * 100;}
   else if (props.operation === 'from_to') {res = (n1 - n2) / n1  * -100;}

   return res.toFixed(2)+'%';
});
</script>

<template>
   <div class="text-xl">
      {{ txt1 }}
      <input type="text" v-model="num1">
      {{ txt2 }}
      <input type="text" v-model="num2">
      =
      <input type="text" :value="answer" class="bg-slate-400">
   </div>
</template>

<style scoped>
[type="text"] {
   width: 100px;
   height: 40px;
   margin-left: 10px;
   margin-right: 10px;
   color: black;
   padding: 6px;
}

[type="text"]:nth-of-type(3) {
   margin-left: 30px;
   width: 160px;
}
</style>
