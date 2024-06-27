<script setup>
import TestComponentVue from './components/TestComponent.vue'

const items = [
  { name: 'Лев', surname: 'Shields', city: 'Ялуторовск' },
  { name: 'Капитон', surname: 'Borer', city: 'Тотьма' },
  { name: 'Вениамин', surname: 'Cummerata', city: 'Самара' },
  { name: 'Прасковья', surname: 'Stokes', city: 'Владикавказ' },
  { name: 'Анжелика', surname: 'Ullrich', city: 'Салават' }
]
</script>

<template>
  <div class="mb-10 bg-red-500">Привет, мир!</div>
  <h1 class="text-3xl font-bold underline">Hello world!</h1>
  <TestComponentVue :items="items" />
</template>

<style></style>
