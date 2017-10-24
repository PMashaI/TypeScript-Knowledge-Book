#### **Название фичи: Decorators**

**Описание**:

Декоратор предназначен для динамического добавления объекту новой функциональности. Является гибкой альтернативой механизму наследования, в том числе и множественного.

Декоратор является оберткой над исходным компонентом. Он реализует тот же самый интерфейс, поэтому может замещать этот компонент. Он добавляет свой код до и/или после вызовов исходных методов, в крайнем случае замещая их полностью. Это приводит к изменению исходного поведения и появлению новых возможностей.

**Детали**:

Декоратор - это особый вид объявления, который может быть прикреплён к объявлению класса, методу / акцессору /свойству / параметру. Декораторы используют форму @expression, где она должна вычислиться в функцию, которая будет вызвана во время исполнения, вместе с информацией декорированного объявления.

**\(!\)** Декораторы -- экспериментальная функция, которая может измениться в будущих релизах.

При вычислении нескольких декораторов на одном объявлении:

1. Выражения для каждого декоратора вычисляются сверху вниз.
2. Результаты затем вызываются как функции снизу вверх.

**Аналог в c\#**: `Decorators`

**Решаемая проблема**:



**Как решить проблему**:



**Синтаксис**[**:**](https://citifox.ru/event/adidas-dance-battle/)

```js
//декоратор

//target – прототип класса, в котором установлен декоратор;
//key – имя метода на котором установлен декоратор;
//value – дескриптор метода, на который установлен декоратор
function decoratorName(target: Function, key: string, value: any) {
    return {
        value: (...args: any[]) => {
            // Код выполняемый до вызова декорируемого метода          

            // Вызов исходного метода
            var result = value.value.apply(this, args);

            // Код выполняемый после вызова декорируемого метода

            return result;
        }
    };
}

//Фабрика Декораторов - функция, возвращающая выражение, которая будет вызвана декоратором во время 
//исполнения программы

function color(value: string) { // фабрика
    return function (target) { // декоратор
        ...
    }
}

// композиция декораторов
function f() {
    return function (target, propertyKey: string, descriptor: PropertyDescriptor) {
        ...
    }
}

function g() {
    return function (target, propertyKey: string, descriptor: PropertyDescriptor) {
        ...
    }
}

class C {
    @f()
    @g()
    method() {}
}

// f(): вычисляется
// g(): вычисляется
// g(): вызван
// f(): вызван
```

**Перекомпилированный в JSкод:**

```js
function color(value) {
    return function (target) {
        ...
    };
}

var __decorate = (this && this.__decorate) || function (decorators, target, key, desc) {
    var c = arguments.length, r = c < 3 ? target : desc === null ? desc = Object.getOwnPropertyDescriptor(target, key) : desc, d;
    if (typeof Reflect === "object" && typeof Reflect.decorate === "function") r = Reflect.decorate(decorators, target, key, desc);
    else for (var i = decorators.length - 1; i >= 0; i--) if (d = decorators[i]) r = (c < 3 ? d(r) : c > 3 ? d(target, key, r) : d(target, key)) || r;
    return c > 3 && r && Object.defineProperty(target, key, r), r;
};
function f() {
    console.log("f(): вычисляется");
    return function (target, propertyKey, descriptor) {
        console.log("f(): вызван");
    };
}
function g() {
    console.log("g(): вычисляется");
    return function (target, propertyKey, descriptor) {
        console.log("g(): вызван");
    };
}
var C = /** @class */ (function () {
    function C() {
    }
    C.prototype.method = function () { };
    __decorate([
        f(),
        g()
    ], C.prototype, "method", null);
    return C;
}());
```



