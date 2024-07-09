<script setup></script>

<template>
  <div
    class="m-auto flex h-screen w-4/5 flex-col items-center justify-center rounded-xl bg-blue-300 shadow-xl"
  >
    <div>
      <h1 class="">Калькулятор копирайтера</h1>
      <label for="textarea" class="mb-2 block text-sm font-medium text-gray-900 dark:text-white"
        >Введите текст в форму и нажмите на «Посчитать»</label
      >
      <textarea
        id="textarea"
        rows="14"
        cols="60"
        class="block w-full resize-none rounded-lg border border-gray-300 bg-gray-50 p-2.5 text-sm text-gray-900 focus:border-blue-500 focus:ring-blue-500 dark:border-gray-600 dark:bg-gray-700 dark:text-white dark:placeholder-gray-400 dark:focus:border-blue-500 dark:focus:ring-blue-500"
        placeholder="Напишите или скопируйте сюда текст..."
      ></textarea>
    </div>

    <div class="mt-5 flex w-1/3 gap-10">
      <div class="flex-col">
        <p>Ставка</p>
        <p>Итоговая сумма</p>
        <p>Количество символов без пробелов</p>
        <p>Количество символов с пробелами</p>
      </div>
      <div class="flex flex-col gap-5">
        <button
          class="select-none rounded-full border border-gray-900 bg-white px-6 py-3 text-center align-middle text-xs font-bold uppercase text-gray-900 transition-all hover:bg-green-500 focus:ring focus:ring-green-400 active:opacity-[0.85]"
          type="button"
        >
          Посчитать
        </button>
        <button
          class="select-none rounded-full border border-gray-900 bg-white px-6 py-3 text-center align-middle text-xs font-bold uppercase text-gray-900 transition-all hover:bg-red-400 focus:ring focus:ring-red-400 active:opacity-[0.85]"
          type="button"
        >
          Очистить
        </button>
      </div>
    </div>
  </div>
</template>
