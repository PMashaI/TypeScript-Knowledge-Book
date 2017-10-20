#### **Название фичи: Namespaces**

**Описание**: Пространства имен предоставляют удобный синтаксис вокруг общего паттерна, используемого в JavaScript.

Пространства имен могут быть вложены. 

**Аналог в js**: `module`

**Синтаксис**[**:**](https://citifox.ru/event/adidas-dance-battle/)

```js
namespace Utility {
    export function log(msg) {
        console.log(msg);
    }
    export function error(msg) {
        console.error(msg);
    }
}
```

**Перекомпилированный в JSкод:**

```js
var Utility;
(function (Utility) {
    function log(msg) {
        console.log(msg);
    }
    Utility.log = log;
    function error(msg) {
        console.error(msg);
    }
    Utility.error = error;
})(Utility || (Utility = {}));
```



