#### **Название фичи: Mixins**

**Описание**:  
TypeScript, как и многие объектно-ориентированные языки, не позволяет использовать напрямую множественное наследование. Из-за этого, не смотря на то, что можно реализовать множество интерфейсов в классе, унаследовать его можно только от одного класса.  
Примесь – объект, содержащий методы и свойства для реализации конкретного функционала.  
Функциональность миксинов \(mixins\) частично позволяет унаследовать свойства и методы сразу двух и более классов, тем самым избавившись от дублирования в коде.

**Аналог в Scala**: `mixins`, `traits`

**Решаемая проблема**:  
В какой-то момент в дочерних классах появляется необходимость в одинаковом функционале из-за чего возникает копипаст и нехватка множественного наследования:  
![](/assets/impor666t.png)

Часто данный функционал не имеет ничего общего с родительскими классами, поэтому выносить его в некий базовый класс может быть нелогично.

**Ограничения**:

* Миксин может унаследовать только те свойства и методы, которые непосредственно определены в применяемом классе, то есть он не будет работать, если применяемый класс наследует какие-то свойства / методы от другого класса.

* Если родительские классы определяют метод с одним и тем же именем, то миксин наследует только тот метод, который копируется в него последним в функции applyMixins.

**Плюсы**:

* Простота реализации;
* Легкость переопределения содержащегося в миксине кода;
* Гибкость подключения, возможность создания зависимых миксинов;
* Использование паттерна не усложняет его понимание и поддержку, так как используется существующий механизм наследования;
* Скорость вмешивания — чтобы замешать миксин подобным образом не требуется ни единого цикла;
* Оптимальное использование памяти \(отсутствие копирования\)

**Как решить проблему**:

Создание временного класса на основе миксина и подстановка его в очередь наследования:

![](/assets/imp43rt.png)

**Синтаксис с примером:**

```js
// одноразовый миксин
class Disposable {
    isDisposed: boolean;
    dispose() {
        this.isDisposed = true;
    }

}

// активируемый миксин
class Activatable {
    isActive: boolean;
    activate() {
        this.isActive = true;
    }
    deactivate() {
        this.isActive = false;
    }
}

// новый класс, объединяющий обе примеси. Рассматриваем классы как интерфейсы и используем только типы, а не реализации
class SmartObject implements Disposable, Activatable {
    constructor() {}

    interact() {
        this.activate();
    }
    
    // создаем свойства-дублёры
    // Disposable
    isDisposed: boolean = false;
    dispose: () => void;

    // Activatable
    isActive: boolean = false;
    activate: () => void;
    deactivate: () => void;
}

//соединяем примеси в классе, создавая полную реализацию
applyMixins(SmartObject, [Disposable, Activatable]);

//функция для создания примесей. Пробегает по свойствам и копировать их в целевой элемент, 
//заполняя свойства-дублёры их реализациями.
function applyMixins(derivedCtor: any, baseCtors: any[]) {
    baseCtors.forEach(baseCtor => {
        Object.getOwnPropertyNames(baseCtor.prototype).forEach(name => {
            derivedCtor.prototype[name] = baseCtor.prototype[name];
        });
    });
}
```

**Перекомпилированный в JSкод:**

```js
var Disposable = /** @class */ (function () {
    function Disposable() {
    }
    Disposable.prototype.dispose = function () {
        this.isDisposed = true;
    };
    return Disposable;
}());
var Activatable = /** @class */ (function () {
    function Activatable() {
    }
    Activatable.prototype.activate = function () {
        this.isActive = true;
    };
    Activatable.prototype.deactivate = function () {
        this.isActive = false;
    };
    return Activatable;
}());
var SmartObject = /** @class */ (function () {
    function SmartObject() {
        this.isDisposed = false;
        this.isActive = false;
    }
    SmartObject.prototype.interact = function () {
        this.activate();
    };
    return SmartObject;
}());
applyMixins(SmartObject, [Disposable, Activatable]);
function applyMixins(derivedCtor, baseCtors) {
    baseCtors.forEach(function (baseCtor) {
        Object.getOwnPropertyNames(baseCtor.prototype).forEach(function (name) {
            derivedCtor.prototype[name] = baseCtor.prototype[name];
        });
    });
}

```

**Больше деталей**: [тут](https://habrahabr.ru/post/255865/)

