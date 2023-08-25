<script setup lang="ts">
  import { ref } from 'vue';
  const header = ref("Shopping list App");
  const items = ref([
    {id:1, label: "poulet"},
    {id:2, label: "ananas"},
    {id:3, label: "Coca"},
  ]);
  const newItem = ref("");
  const newItemHighPriority = ref(false)
</script>

<template>
  <main>
    <h1 class="text-center">{{ header }}</h1>
    <input type="text" placeholder="Add an items" v-model.trim="newItem">
    <label>
      <input type="checkbox" v-model="newItemHighPriority">
      High Priority :
      
    </label>
    <br>
    {{ newItemHighPriority }}
    <ul>
      <li v-for="({id, label}, index) in items" :key="id"> 
        {{ index }}
        {{ label }}
      </li>
    </ul>
  </main>
</template>
