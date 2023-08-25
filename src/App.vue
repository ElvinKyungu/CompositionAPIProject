<script setup lang="ts">
  import { ref } from 'vue';
  const header = ref("Shopping list App");
  const editingItem = ref(false);
  const items = ref([
    // {id:1, label: "poulet"},
    // {id:2, label: "ananas"},
    // {id:3, label: "Coca"},
  ]);
  const newItem = ref("");
  const newItemHighPriority = ref(false)
  const saveItem = ()=>{
    items.value.push({id: items.value.length +1, label: newItem.value})
    newItem.value = ""
  }
  const doEdit = (e)=>{
    editingItem.value = e
    newItem.value = ""
    
  }
</script>

<template>
  <main>
    <div>
      <h1 class="text-center">{{ header }}</h1>
      <button v-if="editingItem" @click="doEdit(false)">
        Cancel
      </button>
      <button v-else  @click="doEdit(true)">
        Add item
      </button>
    </div>
    <form @submit.prevent="saveItem" v-if="editingItem">
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
    <div v-if="!items.length">
      il n'y a rien jusqu'a maintenant ?
    </div>
  </main>
</template>
