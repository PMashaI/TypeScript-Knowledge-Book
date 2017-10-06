### Название фичи: Классы

**Описание**:**  
**Поддержка наследования \(extends\).

Модификаторы `public, private, protected, readonly, static, abstract.`

Поддержка `getter, setter`

**Аналог в c\# / js**: class

**Решаемая проблема:**

**Пример возникновения:**

**Пример кода:**

```js
class Greeter {
    greeting: string;

    constructor(message: string) {
        this.greeting = message;
    }

    greet() {
        return "Hello, " + this.greeting;
    }
}

let greeter = newGreeter("world");
```

**Перекомпилированный в JS код**:

```js
var Greeter = (function(){
    function Greeter(message) {
        this.greeting = message;
    };
    Greeter.prototype.greet = function(){
        return "Hello, " + this.greeting;
    };

    return Greeter;
}());

var greeter = new Greeter("world");
```

**Как решилась проблема**:

