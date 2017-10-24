#### **Название фичи: Generics**

**Описание**:

Обобщённый тип позволяет резервировать место для типа, который будет заменён на конкретный, переданный пользователем, при вызове функции / метода, при работе с классами.

**Совместимость типов**:

В случае, когда для обобщенного типа указаны типовые аргументы, поведение идентично не обобщенному типу.

В случае, когда для обобщенного типа не указаны типовые аргументы, совместимость проверяется, словно в качестве пропущенных типовых аргументов был указан`any`. Полученные типы проверяются на совместимость после так же, как и обычные.

**Аналог в c\# / Java**: `Generics / Templates`

**Решаемая проблема**:

Определение типа аргумента интерфейса / переменной  /класса так, чтобы его впоследствии можно было использовать для последующего использования / описания типа возвращаемого значения.

**Пример возникновения**:

Необходимо захватить тип аргумента функции, чтобы его впоследствии можно было использовать для описания типа возвращаемого значения.

**Пример проблемы на JavaScript + TypeScript без generics:**

```js
var a = identity("Hey!"); //какой тип примет переменная a? 

//JS
function identity(arg){
    return arg;
}

//TS
function identity(arg: any): any {
    return arg; // может быть любой тип any
}
```

**Пример решения на TypeScript:**

```js
let output = identity("Hey!"); // у output будет тип string

function identity<t>(arg: T): T {
    return arg;
}
</t>
```

**Как решить проблему**:

Использование типовой переменной и

**Синтаксис**[**:**](https://citifox.ru/event/adidas-dance-battle/)

```js
function identity<t>(arg: T): T {
    return arg;
}
</t>

let output = identity<string>("myString");  // у output будет тип string
</string>

let output = identity("myString");  // у output будет тип string

//ограничение обобщения
interface Lengthwise {
    length: number;
}
//добавили ограничение на свойство length 
function loggingIdentity<t extends="" lengthwise="">(arg: T): T {
    console.log(arg.length);  // берем только объекты со свойством .length
    return arg;
}
</t>

//совместимость типов
let identity = function<t>(x: T): T {}
 
let reverse = function<U>(y: U): U {}
 
identity = reverse;  // работает, так как (x: any)=>any совпадает с (y:any)=>any
</t>
```

**Перекомпилированный в JSкод:**

```js
function identity(arg) {
    return arg;
}
/t>;

var output = identity("myString"); 
/string>;

function loggingIdentity(arg) {
    console.log(arg.length);
    return arg;
}
/t>;

var identity = function (x) { };
var reverse = function (y) { };
identity = reverse;
/t>;
```



