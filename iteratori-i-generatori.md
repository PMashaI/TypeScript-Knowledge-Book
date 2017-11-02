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

**Ключевое слово yield**

yield используется для паузы или прекращения работы генератора. он может возвращать результат наружу или  передавать значение извне в генератор.

С помощью выражения yield у разработчика появляется возможность передать значение обратно во внешний код. Использовать ключевое слово можно с числами, объектами, callbacks или promises. Задача генератора в данном случае - возвращение выражения внешнему коду как только достигается точка в теле функции.

**Пример на Typescript:**

```js
function* myGenerator() {
   yield "Yo!";
}
```

**Перекомпилированный в JSкод:**

```js
var __generator = (this && this.__generator) || function (thisArg, body) {
    var _ = { label: 0, sent: function() { if (t[0] & 1) throw t[1]; return t[1]; }, trys: [], ops: [] }, f, y, t, g;
    return g = { next: verb(0), "throw": verb(1), "return": verb(2) }, typeof Symbol === "function" && (g[Symbol.iterator] = function() { return this; }), g;
    function verb(n) { return function (v) { return step([n, v]); }; }
    function step(op) {
        if (f) throw new TypeError("Generator is already executing.");
        while (_) try {
            if (f = 1, y && (t = y[op[0] & 2 ? "return" : op[0] ? "throw" : "next"]) && !(t = t.call(y, op[1])).done) return t;
            if (y = 0, t) op = [0, t.value];
            switch (op[0]) {
                case 0: case 1: t = op; break;
                case 4: _.label++; return { value: op[1], done: false };
                case 5: _.label++; y = op[1]; op = [0]; continue;
                case 7: op = _.ops.pop(); _.trys.pop(); continue;
                default:
                    if (!(t = _.trys, t = t.length > 0 && t[t.length - 1]) && (op[0] === 6 || op[0] === 2)) { _ = 0; continue; }
                    if (op[0] === 3 && (!t || (op[1] > t[0] && op[1] < t[3]))) { _.label = op[1]; break; }
                    if (op[0] === 6 && _.label < t[1]) { _.label = t[1]; t = op; break; }
                    if (t && _.label < t[2]) { _.label = t[2]; _.ops.push(op); break; }
                    if (t[2]) _.ops.pop();
                    _.trys.pop(); continue;
            }
            op = body.call(thisArg, _);
        } catch (e) { op = [6, e]; y = 0; } finally { f = t = 0; }
        if (op[0] & 5) throw op[1]; return { value: op[0] ? op[1] : void 0, done: true };
    }
};
function myGenerator() {
    return __generator(this, function (_a) {
        switch (_a.label) {
            case 0: return [4 /*yield*/, "Yo!"];
            case 1:
                _a.sent();
                return [2 /*return*/];
        }
    });
}
```



