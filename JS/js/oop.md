## OOП в JS
    
    Нужно охарактеризовать что такое ООП

    - Что такое ООП
    - Объекты
    - Классы в ES6
    - github TC39 - https://github.com/tc39

## Объекты

### Копирование объектов

```js
    const student = {
        firstName: 'John',
        lastName: 'Dow',
        age: 21
    }
    
    const clones = []
    const count = 10

    // 1) Object.assign()
    for (let i = 0; i < count; i++) {
        const newClone = Object.assign({}, student) // Все сложиться в пустой объект {}
        clones.push(newClone)
    }
    // Подводные камни: свойства и методы передаются по ссылке (то есть не решает проблемы глубокого копирования)

    // 2) Spread оператор
    for (let i = 0; i < count; i++) {
        const newClone = {
            ...student
        }
        
        clones.push(newClone)
    }
    // Подводные камни: плохая поддержка браузерами, не решает проблемы глубокого копирования
    
    // 3) JSON.parse --> JSON.stringify (древний способ)

    // 4) cloneDeep - из lodash
```

### Сравнение объектов
    При сравнении объектов может произойти утиная типизация

```js
    // 1) Добавить признак объекту 
    const student = {
        kind: 'studentMath', // какой-либо признак
        firstName: 'John',
        lastName: 'Dow',
        age: 21
    }
    
    // 2) Функции конструкторы, оператор instanceof
```

## Классы

```js 
    // Часть выражения (не используем на данный момент)
    const Car = class {
        
    }

    // Конструкция (9 из 10)
    class Car {
        constructor(param) {
            console.log(param)
        }
    }
    new Car(param)
    // Примеры: https://codepen.io/mclaren/pen/MWjvWPy

    class Car {
        constructor(param) {
            this._color = param.color // _ подчеркивание это договоренность о том что это приватные свойства или методы
            this._speed = param.speed
        }
        
        static defaultName = 'Tesla' // Статические свойства, на данный момент плохая поддержка браузерами
        
        static createNitro() { // Статический метод родительского класса, ВНИМАНИЕ НЕ передается потомкам, исключительно метод предка
            return new this(newParam)
        }
        // Примеры статических методов: Date.now(), Math.random(), Object.assign()
        
        get settings() { // Например нужно для чтения приватных свойств
            return {
                color: this._color,
                speed: this._speed,
            }
        }
        
        set settings(color) {
            this._color = color
        }
        
        // Геттеры и Сеттеры это утилитарные методы класса их нельзя вызвать, называться должны одинаково
        // settings - без скокобок - Геттер
        // settings = 'blue' - метод присвоения - Сеттер
        
        // Реальные приватные свойства, плохо поддерживатеся в браузерах
        #countDoor
        #countWheel
    }
```

