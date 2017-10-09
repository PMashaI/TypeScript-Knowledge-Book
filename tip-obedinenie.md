#### **Название фичи: Тип объединение**

**Описание:**

Описывает значение, которое может быть одним из нескольких типов. Используется вертикальная черта \(`|`\), чтобы отделить каждый тип.  
**Аналог в c\# / js**: `union`

**Решаемая проблема:**

Разработчику может потребоваться описать тип переменных, который он не знает на момент работы с приложением / компиляции, но который он хотел бы ограничить набором возможных типов.

При этом, если не ограничивать типы, то можно вызвать функцию с различными типами параметра, на что TypeScript не выведет никаких ошибок \(**даже** если по коду, данный тип будет не подходить по коду\).

**Пример возникновения:**

Разработчик получает значения переменной из динамического контента, например от пользователя или от сторонней JS библиотеки и для нее есть набор подходящих типов.

**Пример проблемы на JavaScript:**

```js
function padLeft(value, padding) {
    if(typeof padding !== "number") {
        padding = Number(padding.trim());
    }
    ...
}

let indentedString1 = padLeft("Hello world", 10);     // работает
let indentedString2 = padLeft("Hello world", " 10 "); // работает
let indentedString3 = padLeft("Hello world", true);   // падает: padding.trim is not a function
```

**Пример решения на TypeScript:**

```js
function padLeft(value: string, padding: string | number) {
    // ...
}

let indentedString1 = padLeft("Hello world", 10);
let indentedString2 = padLeft("Hello world", " 10 ");
let indentedString3 = padLeft("Hello world", true);   // выведет ошибку во время компиляции
```

**Перекомпилированный в JSкод:**

```js
function padLeft(value, padding) {
    // ...
}

let indentedString1 = padLeft("Hello world", 10);
let indentedString2 = padLeft("Hello world", " 10 ");
let indentedString3 = padLeft("Hello world", true);
```

**Как решилась проблема**:

Разработчик ограничивает набор типов и позволяет значениям пройти проверку на этапе компиляции.

**Важно учесть:**

Если у нас есть значение типа объединения, вы можете получить доступ только к тем его элементам, которые являются общими для всех типов в объединении.

Иначе говоря, если значение имеет тип A \| B, мы знаем, что оно имеет только те элементы, которые имеют оба A и B.

_Например:_

```js
interface Bird {
    fly();
    layEggs();
}

interface Fish {
    swim();
    layEggs();
}

function getSmallPet(): Fish | Bird {
    // ...
}

let pet = getSmallPet();
pet.layEggs(); // ок
pet.swim();    // ошибка
```

В этом примере Bird имеет элемент именованный fly. Мы не можем быть уверены в том, есть ли у переменной, имеющей тип Bird \| Fish, метод fly. Если переменная во время выполнения на самом деле является Fish, тогда вызов pet.fly\(\) не выполнится.

