### Название фичи: Остаточные параметры

**Описание**:  **  
**Неограниченное число необязательных параметров. При передаче аргументов для остаточных параметров их можно передать столько, сколько угодно; а можно и вообще ничего не передавать.**  
Аналог в c\# / js: **arguments in JS**  
Решаемая проблема:           
**Работа с несколькими параметрами, рассматривая их как группу; неизвестно, сколько параметров будет принимать функция.  
**Пример возникновения:**  
Неизвестно, сколько параметров будет принимать функция.

**Пример кода:**

```js
function buildName (firstName: string, ...restOfName: string[]) {
    return firstName + " "+ restOfName.join("");
}
let employeeName = buildName("Joseph", "Samuel", "Lucas", "MacKinzie");
```

**Перекомпилированный в JS код**:

```js
function buildName(firstName) {
    var restOfName = [];
    for (var _i = 1; _i < arguments.length; _i++) {
        restOfName[_i - 1] = arguments[_i];
    }
    return firstName + " " + restOfName.join("");
}
var employeeName = buildName("Joseph", "Samuel", "Lucas", "MacKinzie");
```

**Как решилась проблема**:**  
**Передача гибкого количества параметров в качестве группы

