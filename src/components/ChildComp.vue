<script setup>
defineProps({
  items: Array
});
</script>

<template>
  <h2>Это дочерний компонент</h2>
  <div>Привет</div>
  <div v-for="item in items" :key="item.id">
    {{ item.name }}
  </div>
</template>
