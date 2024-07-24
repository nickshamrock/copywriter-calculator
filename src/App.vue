<script setup>
import { ref } from 'vue';

import ModalWindow from './components/ModalWindow.vue';
import CalculatePriceMenu from './components/CalculatePriceMenu.vue';

//логика подсчета стоимости текста
const textFromTextarea = ref('');
//получаем очистку поля ввода текста с помощью emit из дочернего компонента CalculatePriceMenu
function clearArea() {
  textFromTextarea.value = '';
}
//условие показа модального окна
const showModal = ref(false);
</script>

<template>
  <div
    class="m-auto flex h-full w-4/5 flex-col items-center rounded-xl bg-blue-300 pb-10 pl-5 pr-5 shadow-xl max-lg:w-full"
    @keydown.esc="showModal = false"
  >
    <div class="flex flex-col items-center">
      <header class="pt-5">
        <h1
          class="mb-2 text-center text-5xl font-bold leading-none tracking-tight text-gray-900 max-md:text-4xl max-sm:text-3xl"
        >
          Калькулятор копирайтера
        </h1>
      </header>
      <label
        for="textarea"
        class="mb-2 flex items-start text-xl font-medium text-gray-900 max-sm:text-center max-sm:text-lg"
        >Введите текст и нажмите на «Посчитать»
        <img
          src="/question-icon.svg"
          alt="question"
          width="22px"
          height="22px"
          class="ml-1 cursor-pointer transition-all duration-500 hover:scale-150"
          @click="showModal = true"
          id="show-modal"
      /></label>
      <!-- модальное поп-ап окно -->
      <ModalWindow :show="showModal" @close="showModal = false"> </ModalWindow>

      <textarea
        id="textarea"
        rows="14"
        class="block w-full resize-none rounded-lg border border-gray-300 bg-gray-50 p-2.5 text-base text-gray-900 max-sm:h-4/6"
        placeholder="Напишите или скопируйте сюда текст..."
        v-model="textFromTextarea"
      ></textarea>
      <!-- меню с расчетом стоимости текста, в props - текст из textarea; в emit - cигнал для удаления текста из textarea-->
      <CalculatePriceMenu :text="textFromTextarea" @makeEmptyArea="clearArea"></CalculatePriceMenu>
    </div>
  </div>
</template>
