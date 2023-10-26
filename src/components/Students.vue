<script setup>
import { onMounted, ref } from 'vue'
import axios from 'axios'
const students = ref([]);
onMounted(()=> {
  axios.get('http://34.82.81.113:3000/students')
  .then((response)=> {
    students.value = response.data;
  });
})
</script>

<template>
  <table class="w-full text-left border-2 bg-slate-300">
    <thead class="border-b bg-slate-300">
      <tr>
        <th>Name</th>
        <th>Group</th>
      </tr>
    </thead>
    <tbody class="bg-slate-200">
      <tr class="border-2" v-for="s in students" :key="s._id">
        <td class="px-6 py-6">{{ s.name }}</td>
        <td>{{ s.group }}</td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
