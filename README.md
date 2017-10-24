**Typescript**

**Решаемая проблема:**

Проблемы с разработкой сложных программ на JavaScript привели к необходимости облегчения разработки компонентов языка. Приложения становились больше, и начали давать о себе знать проблемы JavaScript, связанные с типами данных, с отсутствием единого способа наследования объектов, с моделью памяти JS, а также многое другое. Динамическая природа языка просто подталкивает к написанию универсальных функций, которые могут принимать десятки вариантов аргументов \(как по типу данных, так и по их количеству\).

Разработчики TypeScript искали решение, которое не будет нарушать совместимость со стандартом ECMAScript и его кросс-платформенной поддержкой. TypeScript был основан на поддержке программирования на базе классов, который предлагает стандарт ECMAScript.

TypeScript отличается от JavaScript возможностью явного статического назначения типов: позволяет статически анализировать язык, облегчая IDE поддержку и работу с кодом \(соответственно их легче поддерживать, развивать, масштабировать и тестировать\), поддержкой использования полноценных классов, а также поддержкой подключения модулей, что призвано повысить скорость разработки, облегчить читаемость, рефакторинг и повторное использования кода, помочь осуществлять поиск ошибок на этапе разработки и компиляции, повысить скорость выполнения программ.

Так что же привело к созданию TypeScript:

* Многообразие версий JS поддерживаются не во всех браузерах, TS в свою очередь дает возможность используя различные «плюшки» быть компилируемым в различные версии: JS, ES6, ES5 и т.д.

* Не модульность JavaScript.

* Иногда JavaScript ведёт себя неожиданно для разработчика, что определяется динамической типизацией.

**Специфичность**:

* Является надмножеством JavaScript;

* TS - это всего лишь инструмент, который призван облегчить разработку приложений.

* Позволяет масштабировать разработку сложныхJavaScript приложений. \(Добавляет возможность объявлять модули, классы и интерфейсы.\)

* Согласованность изменений \(ошибки при компиляции если были конфликты в мерже\).

* Компиляция TypeScript происходит при сборке проекта.

В чем **преимущество** перед существующими решениями:

* Строго статически типизированный \(все типы проверяются при компиляции\). Избавляет нас от динамической типизации JS, которая вызывает множество регрессионных ошибок. Поведение кода становится более очевидным.

* Реализует концепции свойственные ООП \(наследование, полиморфизм, инкапсуляция, модификаторы доступа, и т.д.\)

* Open-source проект \([https://github.com/Microsoft/TypeScript](https://github.com/Microsoft/TypeScript)\)

* Кроссплаформенный \(Windows, MasOS, Linux\)

**Похожие инструменты:** JavaScript

**Как работает** \(**специфичность**\):

* Код на TS компилируется в JavaScript

* Генерируемый код поддерживается большинством браузеров \(ориентируется на стандарт ECMAScript 3, также поддерживает ECMAScript 5 и ECMAScript 6. В процессе разработки можно самим задать целевой стандарт ECMAScript.\)

**Что нужно для установки:**

_**Предпочтительные инструменты**_: VisualStudioCode // VisualStudio 2015 / 2017

Компилятор TS можно установить с помощью команды менеджера пакетовnpm, который используется в Node.js:

```node.js
> npm install -g typescript
```

**Quick start: Depending on the technology what we will use together with TS**

TypeScript itself is simple to add to any project with npm.

```js
> npm install -D typescript
```

**Плюсы**

* Описание каждого элемента приложения - сводит к минимуму вероятность неверной реализации / некорректного вызова методов; Заставляет продумать логику до самой реализации; Не дает возможность изменить один кусок приложения, сломав другой;

* Описание области видимости свойств класса - ограничивает разработчика от совершения ошибок;

* Жесткая архитектура дает возможность писать меньше тестов — все параметры методов жестко описаны \(если код скомпилировался, тогда, почти каждый вызов будет является валидным\);

* Возможность настроить проект так, что любой не компилируемый код нельзя будет закоммитить;

**Минусы**

* Для использования внешних инструментов \(библиотек / фреймворков\), сигнатуру каждого из методов каждого модуля этого инструмента необходимо описать, чтобы компилятор не выбрасывал ошибки.

* Небольшая поддержка в виду малого количества специалистов на рынке.

* На разработку тратится больше времени, в сравнении с JavaScript. Вызвано тем, что помимо реализации класса необходимо описать все задействованные интерфейсы, сигнатуры методов.

Какие **возможности** открывает язык:

* Система для работы с модулями / классами — можно создать интерфейсы, модули, классы;

* Можно наследовать интерфейсы \(в том числе множественное наследование\), классы;

* Можно описывать собственные типы данных;

* Можно создавать универсальные-интерфейсы \(generic interfaces\);

* Можно описать тип переменной \(или свойств объекта\), или описать каким интерфейсом должен обладать объект на который ссылается переменная;

* Можно описать сигнатуру метода.

**Что нового привносит TypeScript:**

— Статическая типизация и выведение типов;

— Необязательные аргументы для функций и значения по умолчанию;

— public, private, protect для свойств и методов классов;

— Геттеры и сеттеры для свойств «без головной боли»;

— Декораторы для всего;

— Интерфейсы и абстрактные классы;

— Generics;

— Компилирование в ES5 или даже в ES3 \(с оговорками\).

**И в том числе плюшки ES6:**

— Arrow Functions;

— Классы с единым стилем наследования;

— async/await из ES7;

— Итераторы и Генераторы;

— Многострочные строки с шаблонизацией и тоже «без головной боли» с плюсами и кавычками;

— Управление зависимостями, в том числе и их динамическая загрузка.

