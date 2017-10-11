### Название фичи: Классы

**Описание**:  
Элемент, который описывает абстрактный тип данных и его частичную или полную реализацию. 

Модификаторы `public, private, protected, readonly, static, abstract.`

Поддержка `getter, setter`

**Аналог в c\# / js**: class

**Преимущества**:

* Поддержка наследование \(`extends`\)
* Класс состоит из интерфейса и реализации \(вызов метода-конструктора обязателен\)

**Синтаксис:**

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

let greeter = new Greeter("world");
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



