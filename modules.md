#### **Название фичи: Modules**

**Описание**:

Модулем считается файл с кодом, внутри которого ключевым словом`export`помечаются переменные и функции, которые могут быть использованы снаружи. Другие модули могут подключать их через вызов`import`.

В Typescript модули стандартизированы. Со временем, модули будут поддерживаться браузерами без дополнительных утилит.

**Аналог в c\# / js**: -

**То что нужно знать**:

Ключевое слово `export` можно ставить:

* Перед объявлением переменных / функций / классов;
* Отдельно \(в фигурных скобках указывается, что именно экспортируется\).

**Решаемая проблема**:

Когда приложение сложное и много кода.

**Как решить проблему**:

Организовываем код в модули, экспортируем и импортируем значения. В каждом файле описываем какую-то часть, а в дальнейшем – собираем эти части воедино.

**Синтаксис**[:](https://citifox.ru/event/adidas-dance-battle/)

```js
import {one as item1, two } from "./nums";
import * as numbers from "./nums";

export {VARIABLE as NAME};
export let one = 1;
```

**Перекомпилированный в JSкод:**

```js
define(["require", "exports"], function (require, exports) {
    "use strict";
    Object.defineProperty(exports, "__esModule", { value: true });
    exports.one = 1;
});
```



