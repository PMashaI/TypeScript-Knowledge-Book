#### **Название фичи: Тип объединение**

**Описание:**

Описывает значение, которое может быть одним из нескольких типов. Используется вертикальная черта \(`|`\), чтобы отделить каждый тип.  
**Аналог в c\# / js**: [StructLayoutAttribute](https://msdn.microsoft.com/en-us/library/system.runtime.interopservices.structlayoutattribute%28v=vs.110%29.aspx)

**Решаемая проблема:**

Разработчик с одной стороны не может точно определить единственный тип входящего параметра функции \(например, в один момент времени в него могут передать число, в другой момент - строку\), а с другой стороны ему **хочется** иметь проверку типов на момент компиляции при вызове функции, чтобы её нельзя было вызвать с некорректным типом параметра.

**Пример возникновения:**

Разработчик получает значения переменной из динамического контента, например от пользователя или от сторонней JS библиотеки и для нее есть набор подходящих типов. Функция может работать для нескольких типов входного аргумента, но не для всех возможных JavaScript типов.

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

