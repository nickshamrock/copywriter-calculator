# Что это за сервис и что он умеет 

Калькулятор копирайтера - это сервис, который автоматически подсчитывает количество символов (как с пробелами, так и без) и стоимость текста. 

Этот сервис пригодится всем, кто работает с текстами (авторам, редакторам, корректорам, копирайтерам и др.), чтобы автоматизировать подсчет стоимости текста. Благодаря этому калькулятору копирайтера весь подсчет стоимости текста становится честным, быстрым и прозрачным.

Чтобы рассчитать стоимость текста вручную, сначала нужно скопирать текст, зайти в текстовый редактор (Google Документы, Word), создать файл, ввети скопированный текст и узнать количество символов без пробелов через соответствующие команды или вызовы контекстного меню (см. "Статистика" или Ctrl + Shift + C). 

После этого редактор делит полученное количество символов на 1 000, а затем умножает на ставку (например, 100 рублей за 1 000 символов без пробелов). Весь этот процесс занимает много времени и допускает ошибки в расчетах. Этот сервис нужен, чтобы справедливо посчитать стоимость текста. 

## А правильно ли сервис считает количество символов без пробелов?

Правильно. В ходе тестирования сервиса выяснилось, что подсчет количества символов без пробелов (именно по этому показателю рассчитывается стоимость текста) совпадает с подсчетом символов у других редакторов Word и Google Документы. Более того, сервис также корректно учитывает эмодзи, которые часто добавляют в тексты. Это возможно благодаря следующей функции в Vue 3 на этом проекте: 

```sh
const countWithoutSpaces = computed(() => {
  return props.text.replace(/\s+/gu, '').length;
});
```

На чистом JavaScript это выглядит так: 

```sh

let formInputText = document.querySelector('.input-textarea');
let text = formInputText.value; 
  //записываем в переменную countOfSymbols количество символов без пробелов
let countOfSymbols = text.replace(/\s+/gu, '').length; 

```

Эта функция использует **регулярные выражения /\s+/gu в методе replace**, которые позволяют корректно подсчитать количество символов, включая эмодзи (1 эмодзи - это 2 символа без пробелов).

## Чем этот сервис лучше аналогов? 

В отличие от других аналогов, этот сервис позволяет ввести любой текст в поле <textarea>. То есть другие калькуляторы предлагают рассчитать стоимость только тогда, когда пользователь уже знает количество символов без пробелов. Этот же сервис может сразу и посчитать размер текста (количество символов без пробелов), и его стоимость.  

# Стек используемых технологий 

* Фреймворк Vue 3 (версия 3.4.29)
* Сборщик Vite (версия 5.3.1)
* Фреймворк Tailwind для CSS-стилей (3.4.4), а также плагин prettier-plugin-tailwindcss (версия 0.6.5) для автоматического распределения классов в строгом порядке
* Библиотека GSAP для анимации подсчета количества символов (версия 3.12.5)
* Eslint (версия 8.57.0)
* Prettier (версия 3.3.3)

Подробнее о технологиях можно узнать в файлах проекта (.json)

Также к проекту подключены инструменты разработчика Vue (Vue DevTools
v7.3.2)

# Как запустить проект 

Чтобы запустить проект локально, вам потребуется скачать архив репозитория и открыть папку pet-vue в своем редакторе. Затем введите в консоль следующую команду

```sh
npm install
```

Чтобы открыть проект в бразуере, введите следующую команду 

```sh
npm run dev
```

И перейдите на указанный localhost

Также вы можете запустить проект на CodeSandbox. Для этого перейдите по следующей ссылке

https://codesandbox.io/p/github/nickshamrock/pet-vue/main?import=true&embed=1&file=%2F.eslintrc.cjs

Возможно, потребуется авторизация на сайте. Если после установки зависимостей проект не открывается в окне (например, Preview: 2222, ошибка 502), то кликните
на "Start from the editor" в этом же окне. Проект должен развернуться на dev:5173

Также вы можете оценить калькулятор копирайтера на чистом JavaScript, CSS и HTML по ссылке  

https://github.com/nickshamrock/pet-project

Дизайн и функционал этого калькулятора отличается от сервиса на Vue 3, однако одинаково корректно подсчитывает количество символов в тексте и его стоимость

## Автор 

nickshamrock 

Telegram: @nickshamrock https://t.me/NickShamrock

E-mail: nickshamrock1997@gmail.com 
