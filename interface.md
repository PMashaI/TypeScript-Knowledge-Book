### **Название фичи: Интерфейсы**

**Описание**:  
Интерфейс определяет свойства и методы, которые объект должен реализовать. Интерфейсы определяются с помощью ключевого слова interface. Используется как альтернатива множественного наследования. Позволяет заложить структуру класса: имена методов, списки аргументов, возвращаемые типы, но только не тела методов.

**Аналог в c\# / js**: `interface`

**Решаемая проблема:**  
Наложение ряда ограничений на объект.

**Пример возникновения**:  
Передача в функцию аргументов в виде объекта, в котором указаны всего несколько свойств.

**Преимущества:**

* Возможность объявить опциональное свойство \(помечается «**?»**\)
* Возможность добавления свойства только дл чтения \(readonly\)
* Классы могут реализовывать интерфейсы \(implements\)
* Интерфейсы могут наследоваться как и классы \(extends\)
* Интерфейсы массивов позволяют описывать объекты, к которым можно обращаться по заданному индексу \(см. пример\)
* Гибридные интерфейсы \(применяться сразу как к определению объекта, так и к определению функции\)

**Пример проблемы на JavaScript:**

Обычный интерфейс:

```js
function printLabel(labelledObj) {
    console.log(labelledObj.label);
}

var myObj = { size: 10, label: "Size 10 Object" };
printLabel(myObj);
```

Интерфейс массива:

```js
var colors = {};
colors["red"] = "#ff0000";
colors["green"] = "#00ff00";
colors["blue"] = "#0000ff";
```

**Пример решения на TypeScript:**

Обычный интерфейс:

```js
interface LabelledValue {
    label: string;
}

function printLabel(labelledObj: LabelledValue) {
    console.log(labelledObj.label);
}

let myObj = {
    size: 10,
    label: "Size 10 Object"
};

printLabel(myObj);
```

Интерфейс массива:

```js
interface Dictionary {
    [index: string]: string;
}

var colors: Dictionary = {};

colors["red"] = "#ff0000";
colors["green"] = "#00ff00";
colors["blue"] = "#0000ff";

console.log(colors["red"]);
```

**Как решить проблему**: Создать объект, который реализует интерфейс.

**Синтаксис**: при компиляции интерфейс исчезает

