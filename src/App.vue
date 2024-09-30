<script setup>
import { ref } from 'vue';

import ModalWindow from './components/ModalWindow.vue';
import CalculatePriceMenu from './components/CalculatePriceMenu.vue';
import QuestionIcon from './components/icons-for-close-open/QuestionIcon.vue';

const textFromTextarea = ref('');

function clearArea() {
  textFromTextarea.value = '';
}

const showModal = ref(false);
</script>

<template>
  <main class="m-auto flex h-full w-full flex-col items-center px-5 pb-10">
    <section class="relative flex flex-col items-center">
      <header class="pt-5">
        <h1 class="mb-2 text-center text-5xl text-gray-900 max-md:text-4xl max-sm:text-3xl">
          Калькулятор копирайтера
        </h1>
      </header>
      <div class="mb-2 flex gap-1">
        <label for="textarea" class="text-xl text-gray-900 max-sm:text-center max-sm:text-lg"
          >Введите текст и нажмите на «Посчитать»
        </label>

        <QuestionIcon @click="showModal = true" />
      </div>

      <ModalWindow :show="showModal" @close="showModal = false"> </ModalWindow>

      <textarea
        id="textarea"
        rows="12"
        class="w-full resize-none rounded-lg p-2.5 text-base text-gray-900"
        placeholder="Напишите или скопируйте сюда текст..."
        v-model="textFromTextarea"
      ></textarea>
      <CalculatePriceMenu :text="textFromTextarea" @makeEmptyArea="clearArea"></CalculatePriceMenu>
    </section>
  </main>
</template>
