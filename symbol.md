#### **Название фичи: Symbol**

**Описание**:

Тип `symbol` — примитивный тип данных \(как number и string\). Значения создаются с помощью вызова конструктора Symbol.

Они неизменяемы и уникальны и могут быть использованы как ключи для свойств объекта.  
Также их можно использовать вместе с вычисляемыми свойствами, чтобы объявлять свойства объектов и члены классов.

Кроме символов, определяемых пользователем, существуют заранее определенные встроенные символы, которые нужны для отражения внутреннего поведения языка \(`Symbol.hasInstance`, `Symbol.iterator`, `Symbol.replace` и т.д.\).

**Аналог в c\# / js**: -

**Решаемая проблема:**

Необходимо создать и использовать уникальный идентификатор для свойств объекта, а также создать уникальные константы, которые были бы не видны в итерациях `for...in, Object.keys()` или `JSON.stringify()`.

**Синтаксис**[**:**](https://citifox.ru/event/adidas-dance-battle/)

```js
const CHINESE = Symbol(); // в качестве константы

let sym = Symbol();
 
let obj = {
    [sym]: "value"
};
 
console.log(obj[sym]); // value
```

**Перекомпилированный в JSкод:**

```js
var CHINESE = Symbol(); // в качестве константы
var sym = Symbol();
var obj = (_a = {},
    _a[sym] = "value",
    _a);
console.log(obj[sym]); // value
var _a;
```



