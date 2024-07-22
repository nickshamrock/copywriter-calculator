<script setup>
import { ref, watch, reactive, computed } from 'vue';
import gsap from 'gsap';
//получаем из родительского компонента текст, введеный textarea
const props = defineProps({
  text: String
});
const countWithoutSpaces = computed(() => {
  return props.text.replace(/\s+/gu, '').length;
});
const countWithSpaces = computed(() => {
  return props.text.length;
});
const price = ref(100);
const priceForText = ref('кликните на «Посчитать»');
//функция подсчета стоимости за текст без пробелов
function getPriceForText() {
  let result = (countWithoutSpaces.value / 1000) * price.value;
  priceForText.value = result.toFixed(2) + ' руб.';

  if (props.text === '') {
    priceForText.value = 'Сначала введите текст!';
  }
}
//функция очистки поля ввода текста c передачей в родительский компонент
const emit = defineEmits(['makeEmptyArea']);
const emptyLine = '';
function clearTextArea() {
  emit('makeEmptyArea', emptyLine);
  priceForText.value = 'Введите текст';
}
//анимация количества символов без пробелов в поле span + computed полученных значений
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
//анимация количества символов с пробелами в поле span + computed полученных значений
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
</template>
