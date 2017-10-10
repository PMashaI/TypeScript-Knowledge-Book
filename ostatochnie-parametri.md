### Название фичи: Остаточные параметры

**Описание**:  
Неограниченное число необязательных параметров. При передаче аргументов для остаточных параметров их можно передать столько, сколько угодно; а можно и вообще ничего не передавать.**  
Аналог в c\# / js**: `arguments`**  
Решаемая проблема**:  
Работа с несколькими параметрами, рассматривая их как группу; неизвестно, сколько параметров будет принимать функция.  
**Пример возникновения:**  
Неизвестно, сколько параметров будет принимать функция.

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
Передача гибкого количества параметров в качестве группы

