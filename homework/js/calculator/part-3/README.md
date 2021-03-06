# Калькулятор. Часть 3. Обработка событий

Теперь, когда разметка готова, можно приступить к программированию.
И начнём мы с того, что увидим наконец, как в реальной жизни применяется
паттерн "Наблюдатель".

Но для начала нужно узнать кое-что новое - как работать с элементами на странице?
А точнее, как их хотя бы получать.

## Взаимодействие с DOM

[DOM](https://developer.mozilla.org/ru/docs/DOM/DOM_Reference/%D0%92%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5) 
\- document object model - не часть javascript-а, это браузерный API 
(application programming interface), иными словами - набор функций, свойств и т д, 
для взаимодействия с частью браузера.

Самый простой способ получить элемент - обратиться к нему по уникальному идентификатору. Например:

```js
const element = document.getElementById('someElementId');
```

Теперь, если на странице присутствует элемент с аттрибутом `id`, установленным в `someElementId`,
тогда переменная `element` получит на него ссылку.

И сейчас с этим элементом мы можем делать что угодно.

## Обработка событий

Вторым важным пунктом для реализации наших задач является реагирование на действия пользователя.
Чаще всего это клик мышки, ввод текста, и многие другие события.

Для добавления "слушателя" (да-да, паттерн Наблюдатель во всей красе), существует метод
`addEventListener`. Однако его нельзя просто взять и вызвать, как обычную функцию. Этот метод
доступен относительно элементов(и не только).

Метод чаще всего вызывают с двумя аргументами:
1. Событие, на которое мы хотим подписаться
2. Функция, которая должна выполниться при наступлении события

```js
const element = document.getElementById('someElementId');

element.addEventListener('click', function() {
    console.log('Click!');
});
```

Теперь, каждый раз, когда по элементу будет происходить клик, в консоль будет выводиться
соответствующее сообщение.

## Задача

Добавить обработчики кликов на команды и на цифры. При клике в `alert` окне
должен выводиться текст кнопки, по которой произошёл клик.

_* Со звёздочкой:_

Если у вас, как однажды у меня, при решении подобной задачи, не отсохли руки
добавлять идентификаторы для каждой кнопки, то вы хотя бы задались вопросом,
можно ли уменьшить количество кода?

Найдите способ уменьшить количество кода. Прочитайте, что такое _делегирование 
событий_. Если удалось во всём разобраться - реализуйте в ответе на эту задачу.
