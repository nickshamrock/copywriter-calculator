<script setup></script>

<template>
  <div
    class="m-auto mt-5 flex h-fit w-4/5 flex-col items-center justify-center rounded-xl bg-blue-300 p-10 shadow-xl max-md:mt-0 max-md:w-full max-sm:mt-0 max-sm:w-full"
  >
    <div class="flex flex-col items-center">
      <h1
        class="mb-4 text-center text-4xl font-bold leading-none tracking-tight text-gray-900 md:text-5xl lg:text-6xl dark:text-white"
      >
        Калькулятор копирайтера
      </h1>
      <label
        for="textarea"
        class="mb-2 block text-xl font-medium text-gray-900 max-sm:text-sm dark:text-white"
        >Введите текст и нажмите на «Посчитать»</label
      >
      <textarea
        id="textarea"
        rows="14"
        class="block w-full resize-none rounded-lg border border-gray-300 bg-gray-50 p-2.5 text-sm text-gray-900 focus:border-blue-500 focus:ring-blue-500 dark:border-gray-600 dark:bg-gray-700 dark:text-white dark:placeholder-gray-400 dark:focus:border-blue-500 dark:focus:ring-blue-500"
        placeholder="Напишите или скопируйте сюда текст..."
      ></textarea>
    </div>

    <div class="mt-5 flex justify-between gap-[55px] max-sm:flex-col max-sm:gap-4">
      <div class="flex flex-col gap-3">
        <p>
          Ставка:
          <input
            type="number"
            min="0"
            value="100"
            autocomplete="off"
            placeholder="Введите сумму"
            class="ml-2 mr-2 w-16 rounded-xl p-1"
          />₽ за 1 000 символов без пробелов
        </p>

        <p>
          Итоговая сумма:
          <span class="inline-block rounded-xl bg-white p-2">кликните на «Посчитать»</span>
        </p>
        <p>
          Кол-во символов <strong>без пробелов</strong>:
          <span class="inline-block rounded-xl bg-white p-2">0</span>
        </p>
        <p>
          Кол-во символов с пробелами: <span class="inline-block rounded-xl bg-white p-2">0</span>
        </p>
      </div>
      <div class="flex flex-col justify-center gap-5">
        <button
          class="select-none rounded-full border border-gray-900 bg-white px-6 py-3 text-center align-middle text-xs font-bold uppercase text-gray-900 transition-all hover:bg-green-500 focus:ring focus:ring-green-400 active:opacity-[0.85]"
          type="button"
        >
          Посчитать
        </button>
        <button
          class="select-none rounded-full border border-gray-900 bg-white px-6 py-3 text-center align-middle text-xs font-bold uppercase text-gray-900 transition-all hover:bg-red-400 focus:ring focus:ring-red-400 active:opacity-[0.85]"
          type="reset"
        >
          Очистить
        </button>
      </div>
    </div>
  </div>
</template>
