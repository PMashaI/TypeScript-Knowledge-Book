### **Название фичи: Enum\(Перечисления\)**

**Описание:**

Способ задания понятных имен набору численных значений. Перечисления позволяют определить набор именованных числовых констант. Они определяются используя ключевое слово enum.

_**СМОТРИ **_[http://typescript-lang.ru/docs/Enums.html](http://typescript-lang.ru/docs/Enums.html)

**  
Аналог вc\# /js: **`Enumerable`**  
Решаемая проблема:  
Пример возникновения:  
Пример кода:**

```js
enum Color {Red = 1, Green = 2, Blue = 4};

let c: Color = Color.Green;
```

**Перекомпилированный в JS код:**

```js
var Color;

(function (Color) {

Color[Color["Red"] = 1] = "Red";

Color[Color["Green"] = 2] = "Green";

Color[Color["Blue"] = 4] = "Blue";

})(Color || (Color = {}));

var c = Color.Green;
```

**  
Как решилась проблема:**

