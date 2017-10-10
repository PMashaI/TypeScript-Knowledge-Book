### Название фичи: Остаточные параметры

**Описание**:  
Неограниченное число необязательных \(типизированных\) параметров. При передаче аргументов для остаточных параметров их можно передать столько, сколько угодно; а можно и вообще ничего не передавать.**  
Аналог в c\# / js**: `arguments`**  
Решаемая проблема**:  
Работа с несколькими параметрами, рассматривая их как группу; неизвестно, сколько параметров будет принимать функция.  
**Пример возникновения:**  
Неизвестно, сколько типизированных параметров будет принимать функция.

**Пример проблемы в JavaScript**:

```js
function buildName(firstName) {
    var result;
    for (var _i = 1; _i < arguments.length; _i++) {
        result = arguments[_i]++;
    }

    console.log(result);
    console.log(firstName.slice(1));
}

buildName("Jo", 1, 234); // работает
buildName(123, 1, "Jo"); // Падает в runtime: firstName.slice is not a function
```

**Решение в TypeScript**:

```js
function buildName(firstName: string, ...restOfName: number[]) {
    var result;
    for (var _i = 1; _i < arguments.length; _i++) {
        result = arguments[_i]++;
    }

    console.log(result);
    console.log(firstName.slice(1));
}

buildName("Jo", 1, 234); // работает
buildName(123, 1, "Jo"); // выведет ошибку во время компиляции
```

**Как решилась проблема**:  
Передача гибкого количества типизированных параметров в качестве группы.

**Синтаксис**:

```js
function example(firstArg: number, ...restArgs: string[]){
    ...
}
```

**Перекомпилированный в JavaScript код**:

```js
function a(firstArg) {
    var restArgs = [];
    for (var _i = 1; _i < arguments.length; _i++) {
        restArgs[_i - 1] = arguments[_i];
    }
}

```



