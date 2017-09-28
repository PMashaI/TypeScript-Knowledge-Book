### **Название фичи: Классы**

**Описание:      
**Поддержка наследования \(extends\).

Модификаторы public, private, protected, readonly, static, abstract.

Поддержка getter, setter

**Аналог в c\#/js: **class

**Решаемая проблема:**

**Пример возникновения:**

**Пример кода:**

`class Greeter {`

```
greeting: string;

constructor(message: string) {

this.greeting = message;
```

`}`

```
greet() {

    return "Hello, " + this.greeting;

 }
```

`}`

`let greeter = newGreeter("world");`

**  
Перекомпилированный в JS код:**

![](file:///C:\Users\MPCHEL~1\AppData\Local\Temp\msohtmlclip1\01\clip_image001.png)![](/assets/saimport.png)

**Как решилась проблема: **

