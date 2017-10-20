#### **Название фичи: Итераторы и генераторы \(**Оператор`for..of`**\)**

**Описание**:

Итерируемым является такой объект, который содержит реализацию свойства [`Symbol.iterator`](http://typescript-lang.ru/docs/Symbols.html#symboliterator).

Для перебора такого объекта в цикле `for..of` вызывается свойство Symbol.iterator. Возвращает список значений числовых свойств объекта. В первую очередь предназначен для получения значений.  
for..in, в свою очередь, возвращает список ключей итерируемого объекта.

**Аналог в c\# / js**: `for`

**Решаемая проблема:**

Поддержка `Array, Map, Set, String, Int32Array, Uint32Array` и т.д., типов для использования `for..of` и `for...in`

**Как решилась проблема**:

Добавилась поддержка перечисленных типов.

**Синтаксис**[**:**](https://citifox.ru/event/adidas-dance-battle/)

```js
let someArray = [1, "string", false];

for (let entry of someArray) {
    console.log(entry); // 1, "string", false
}

for (let i in list) {
   console.log(i); // "0", "1", "2",
}
```

**Перекомпилированный в JSкод:**

```js
var someArray = [1, "string", false];
for (var _i = 0, someArray_1 = someArray; _i < someArray_1.length; _i++) {
    var entry = someArray_1[_i];
    console.log(entry);
}

for (var i in list) {
    console.log(i); // "0", "1", "2",
}
```



