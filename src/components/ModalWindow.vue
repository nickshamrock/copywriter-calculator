<script setup>
defineProps({
  show: Boolean
});
</script>

<template>
  <Transition name="modal">
    <div
      class="fixed left-0 top-0 z-50 flex h-full w-full overflow-y-auto bg-black/55 transition-opacity duration-500 ease-out"
      v-show="show"
    >
      <div
        class="modal-container m-auto w-3/4 rounded-xl bg-white p-5 transition-all duration-500 ease-in"
      >
        <div class="mb-2 flex justify-between">
          <h2 class="text-xl font-semibold text-black">Зачем нужен этот калькулятор</h2>
          <img
            src="/closeModal-icon.svg"
            width="35px"
            height="35px"
            class="block cursor-pointer transition-all duration-500 hover:scale-150"
            alt="closeModalWindow"
            @click="$emit('close')"
          />
        </div>

        <p>
          Обычно стоимость текста рассчитывают вручную через эту формулу:
          <span class="font-semibold"> (кол-во символов без пробелов / 1000) * ставка</span> за 1
          000 символов без пробелов. Редактору приходится проверять, правильно ли он посчитал
          символы, вспоминать ставку и тратить время на расчеты. Этот сервис полностью
          автоматизирует и ускоряет процесс подсчета, а также избавляет от ошибок в расчетах.
        </p>

        <p class="mt-5">Автор: nickshamrock</p>
        <p>Telegram: @nickshamrock</p>
        <p>Почта: nickshamrock@gmail.com</p>
      </div>
    </div>
  </Transition>
</template>

<style scoped>
.modal-enter-from {
  opacity: 0;
}

.modal-leave-to {
  opacity: 0;
}

.modal-enter-from .modal-container,
.modal-leave-to .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
</style>
