# Калькулятор. Часть 6. Рефакторинг

Фу, не знаю как у вас, а моя релизация получилась очень 
[мусорной и некрасивой](../part-5/answer/index.js).

Вот пункты, которые, на мой взгляд нужно исправить:

* Одним из первых моментов уже при реализации мне бросилось то, что
две функции, которые я добавил, основываясь на своём списке задач,
оказались фактически бесполезными: `changeElementPlaceholderText` и
`calc`. Во-первых, у них относительно отвратные имена; во-вторых -
их тело занимает ровно одну строку и не делает ничего сложного,
а значит можно обойтись и без этих функций.

* Ещё один из самых больших косяков - чтение текущего значения
аргументов непосредственно из элемента, с использованием 
`textContent`. Когда мы сохраняли данные в кнопках, используя 
data атрибуты, это ещё куда ни шло, но оттуда мы только читали,
а в случае аргументов мы и читаем и пишем. Это не смертельно плохо,
но и не очень хорошо. Мы тратим время на обращение к элементу, на
чтение данных из свойства. Гораздо удобнее хранить данные где-то в 
javascript, не правда ли? Думаю, что простых переменных нам будет
достаточно. Текущее решение также изобилует лишним кодом для 
приведения значения `textContent` из `arg1` и `arg2` к
числу. А если кто-то, умный используя отладчик, вставил текст
вместо цифр?

## Задача

Самостоятельно найти огрехи в своём решении, а также те, 
которые будут указаны при code review и исправить их.