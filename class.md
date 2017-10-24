### Название фичи: Классы

**Описание**:  
Элемент, который описывает абстрактный тип данных и его частичную или полную реализацию.

Классы работают подобно интерфейсам, но с одним исключением: у них есть тип статической части и тип экземпляра. При сравнении двух объектов, которые имеют классовый тип, сравниваются только члены экземпляра. Статические члены и конструкторы не влияют на совместимость.

Модификаторы `public, private, protected, readonly, static, abstract.`

Поддержка `getter, setter`

При сравнении двух объектов классового типа, сравниваются только члены экземпляра. Статические члены и конструкторы не влияют на совместимость.

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

//совместимость типов
class Animal {
    feet: number;
    constructor(name: string, numFeet: number) { }
}
 
class Size {
    feet: number;
    constructor(numFeet: number) { }
}
 
let a: Animal;
let s: Size;
 
a = s;  // работает
s = a;  // работает
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

var Animal = /** @class */ (function () {
    function Animal(name, numFeet) {
    }
    return Animal;
}());
var Size = /** @class */ (function () {
    function Size(numFeet) {
    }
    return Size;
}());
var a;
var s;
a = s;
s = a;
```



