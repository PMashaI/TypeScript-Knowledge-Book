#### **Название фичи: Generics**

**Описание**:

Обобщённый тип позволяет резервировать место для типа, который будет заменён на конкретный, переданный пользователем, при вызове функции / метода, при работе с классами.

**Аналог в c\# / Java**: `Generics / Templates`

**Решаемая проблема**:

Определение типа аргумента функции / метода /класса так, чтобы его впоследствии можно было использовать для последующего использования / описания типа возвращаемого значения.

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
```

**Перекомпилированный в JSкод:**

```js
function identity(arg) {
    return arg;
}
/t>;

var output = identity("myString"); 
/string>;

var output = identity("myString");
```



