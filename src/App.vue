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
  const saveItem = ()=>{
    items.value.push({id: items.value.length +1, label: newItem.value})
    newItem.value = ""
  }
</script>

<template>
  <main>
    <h1 class="text-center">{{ header }}</h1>
    <form @submit.prevent="saveItem">
      <input 
        type="text" 
        placeholder="Add an items" 
        v-model.trim="newItem"
      >
      <label>
        <input 
          type="checkbox" 
          v-model="newItemHighPriority"
        >
        High Priority :
      </label>
      <button>
        Ajouter 
      </button>
    </form>
    <br>
    <ul>
      <li v-for="({id, label}, index) in items" :key="id"> 
        {{ index }}
        {{ label }}
      </li>
    </ul>
  </main>
</template>
