<script setup lang="ts">
  import { ref } from 'vue';
  const header = ref("Shopping list App");
  const items = ref([
    {id:1, label: "poulet"},
    {id:2, label: "ananas"},
    {id:3, label: "Coca"},
  ]);
  const newItem = ref("");
  const newItemPriority = ref('low')
</script>

<template>
  <main>
    <h1 class="text-center">{{ header }}</h1>
    <input type="text" placeholder="Add an items" v-model.trim="newItem">
    {{ newItem }}
    Priority :
    <label>
      <input type="radio" v-model="newItemPriority" value="low">
      Low
    </label>
    <label>
      <input type="radio" v-model="newItemPriority" value="high">
      High
    </label>
    <br>
    {{ newItemPriority }}
    <ul>
      <li v-for="({id, label}, index) in items" :key="id"> 
        {{ index }}
        {{ label }}
      </li>
    </ul>
  </main>
</template>
