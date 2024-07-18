<script setup>
import { computed, reactive, ref, watch } from 'vue';
import gsap from 'gsap';

import ModalWindow from './components/ModalWindow.vue';

//логика подсчета стоимости текста
const textFromTextarea = ref('');

const countWithoutSpaces = computed(() => {
  return textFromTextarea.value.replace(/\s+/gu, '').length;
});

const countWithSpaces = computed(() => {
  return textFromTextarea.value.length;
});

const price = ref(100);

const priceForText = ref('кликните на «Посчитать»');

function getPriceForText() {
  let result = (countWithoutSpaces.value / 1000) * price.value;
  priceForText.value = result.toFixed(2) + ' руб.';

  if (textFromTextarea.value === '') {
    priceForText.value = 'Сначала введите текст!';
  }
}
//функция очистки поля ввода текста
function clearTextArea() {
  textFromTextarea.value = '';
}

const showModal = ref(false);
//анимация количества символов без пробелов в поле span
const numberForWithoutSpaces = ref(countWithoutSpaces);
const tweenedForWithoutSpaces = reactive({
  number: 0
});

watch(numberForWithoutSpaces, (n) => {
  gsap.to(tweenedForWithoutSpaces, { duration: 0.5, number: Number(n) || 0 });
});

const animatedCountWithoutSpaces = computed(() => {
  return tweenedForWithoutSpaces.number.toFixed(0);
});
//анимация количества символов с пробелами в поле span
const numberForWithSpaces = ref(countWithSpaces);
const tweenedForWithSpaces = reactive({
  number: 0
});

watch(numberForWithSpaces, (n) => {
  gsap.to(tweenedForWithSpaces, { duration: 0.5, number: Number(n) || 0 });
});

const animatedCountWithSpaces = computed(() => {
  return tweenedForWithSpaces.number.toFixed(0);
});
</script>

<template>
  <div
    class="m-auto flex h-full w-4/5 flex-col items-center rounded-xl bg-blue-300 pb-5 pl-5 pr-5 shadow-xl max-lg:w-full"
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

      <ModalWindow :show="showModal" @close="showModal = false"> </ModalWindow>

      <textarea
        id="textarea"
        rows="14"
        class="block w-full resize-none rounded-lg border border-gray-300 bg-gray-50 p-2.5 text-base text-gray-900 max-sm:h-4/6"
        placeholder="Напишите или скопируйте сюда текст..."
        v-model="textFromTextarea"
      ></textarea>
    </div>

    <div class="mt-5 flex justify-between gap-[15px] max-sm:flex-col max-sm:gap-4">
      <div class="flex flex-col gap-3">
        <p class="text-lg">
          Ставка:
          <input
            type="number"
            min="0"
            value="100"
            autocomplete="off"
            placeholder="Введите сумму"
            class="ml-2 mr-2 w-16 rounded-xl p-1 text-lg"
            id="input-for-price"
            v-model="price"
          />₽ за 1 000 символов без пробелов
        </p>

        <p class="text-lg">
          Итоговая сумма:
          <span class="inline-block rounded-xl bg-white p-2 text-lg">
            {{ priceForText }}
          </span>
        </p>
        <p class="text-lg">
          Кол-во символов без пробелов:
          <span class="inline-block rounded-xl bg-white p-2 text-lg">{{
            animatedCountWithoutSpaces
          }}</span>
        </p>
        <p class="text-lg">
          Кол-во символов с пробелами:
          <span class="inline-block rounded-xl bg-white p-2 text-lg">{{
            animatedCountWithSpaces
          }}</span>
        </p>
      </div>
      <div class="flex flex-col justify-center gap-5">
        <button
          class="select-none rounded-full border border-gray-900 bg-white px-6 py-3 text-center align-middle text-base font-bold uppercase text-gray-900 transition-all hover:bg-green-500 focus:ring focus:ring-green-400 active:opacity-[0.85]"
          type="button"
          @click="getPriceForText"
        >
          Посчитать
        </button>
        <button
          class="select-none rounded-full border border-gray-900 bg-white px-6 py-3 text-center align-middle text-base font-bold uppercase text-gray-900 transition-all hover:bg-red-400 focus:ring focus:ring-red-400 active:opacity-[0.85]"
          type="reset"
          @click="clearTextArea"
        >
          Очистить
        </button>
      </div>
    </div>
  </div>
</template>
