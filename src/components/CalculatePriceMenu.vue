<script setup>
import { ref, watch, reactive, computed } from 'vue';
import gsap from 'gsap';

const props = defineProps({
  text: String
});

const price = ref(100);
const priceForText = ref('кликните на «Посчитать»');

const countWithoutSpaces = computed(() => props.text.replace(/\s+/gu, '').length);
const countWithSpaces = computed(() => props.text.length);

function getPriceForText() {
  if (!props.text) {
    priceForText.value = 'Сначала введите текст!';
    return;
  }
  const result = (countWithoutSpaces.value / 1000) * price.value;
  priceForText.value = `${result.toFixed(2)} руб.`;
}

const emit = defineEmits(['makeEmptyArea']);
function clearTextArea() {
  emit('makeEmptyArea', '');
  priceForText.value = 'Введите текст';
}

const createAnimatedCount = (count) => {
  const tweened = reactive({ number: 0 });

  watch(count, (newValue) => {
    gsap.to(tweened, { duration: 0.5, number: Number(newValue) });
  });

  return computed(() => tweened.number.toFixed(0));
};

const animatedCountWithoutSpaces = createAnimatedCount(countWithoutSpaces);
const animatedCountWithSpaces = createAnimatedCount(countWithSpaces);
</script>

<template>
  <div class="mt-5 flex justify-between gap-[15px] max-sm:flex-col max-sm:gap-4">
    <div class="flex flex-col gap-3 text-lg">
      <p>
        Ставка:
        <input
          type="number"
          min="0"
          value="100"
          placeholder="Введите сумму"
          class="ml-2 mr-2 w-16 rounded-xl p-1"
          id="input-for-price"
          v-model="price"
        />₽ за 1 000 символов без пробелов
      </p>

      <p>
        Итоговая сумма:
        <span class="inline-block rounded-xl bg-white p-2">
          {{ priceForText }}
        </span>
      </p>
      <p>
        Кол-во символов без пробелов:
        <span class="inline-block rounded-xl bg-white p-2">{{ animatedCountWithoutSpaces }}</span>
      </p>
      <p>
        Кол-во символов с пробелами:
        <span class="inline-block rounded-xl bg-white p-2">{{ animatedCountWithSpaces }}</span>
      </p>
    </div>
    <div class="flex flex-col justify-center gap-5">
      <button
        class="rounded-full bg-white px-6 py-3 text-base font-bold uppercase hover:bg-green-400 active:bg-green-600"
        type="button"
        @click="getPriceForText"
      >
        Посчитать
      </button>
      <button
        class="rounded-full bg-white px-6 py-3 text-base font-bold uppercase hover:bg-red-400 active:bg-red-600"
        @click="clearTextArea"
      >
        Очистить
      </button>
    </div>
  </div>
</template>
