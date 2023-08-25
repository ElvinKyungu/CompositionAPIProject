<script setup lang="ts">
  import { ref } from 'vue';
  const header = ref("Shopping list App");
  const items = ref([
    {id:1, label: "poulet"},
    {id:2, label: "ananas"},
    {id:3, label: "Coca"},
  ])
</script>

<template>
  <main>
    <h1 class="text-center">{{ header ? header: "Salut" }}</h1>
    <ul>
      <li v-for="item in items" :key="item.id"> {{ item.label }}</li>
    </ul>
  </main>
</template>
