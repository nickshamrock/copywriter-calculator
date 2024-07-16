<template>
  <div class="fixed z-50 h-full w-full overflow-y-auto overflow-x-hidden bg-neutral-900/50">
    <div class="m-auto flex h-full w-3/4 items-center">
      <div class="rounded-xl bg-white p-5">
        <div class="mb-3 flex justify-between">
          <h2 class="text-xl font-semibold text-black">Зачем нужен этот калькулятор</h2>
          <img
            src="/closeModal-icon.svg"
            width="35px"
            height="35px"
            class="block cursor-pointer"
            alt="closeModalWindow"
            @click="$emit('close')"
          />
        </div>
        <p>
          Обычно стоимость текста рассчитывают вручную через эту формулу:
          <span class="font-semibold"> (кол-во символов без пробелов / 1000) * ставка</span> за 1
          000 символов без пробелов. Редактору приходится проверять, правильно ли он посчитал
          символы, вспоминать ставку и тратить время на расчеты. Этот сервис полностью
          автоматизирует этот процесс, а также избавляет от ошибок в расчетах.
        </p>

        <p class="mt-5">Автор: nickshamrock</p>
        <p>Telegram: @nickshamrock</p>
      </div>
    </div>
  </div>
</template>

<!-- transition all 0.3s ease 0s transform: translate(0px, -100%) -->
