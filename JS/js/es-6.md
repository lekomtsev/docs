## ECMAScript2015 (6th Edition)
    
    ES2015, ES6 или Harmony
    Принят: 17 июня 2015

## Список изменений
     
    - Устранение проблемных концепций
    - Улучшение всроенных в язык объектов
    - Новые возможности
    - Изменение к подходу обновления спецификации
    
## Объявления переменных с помощью const и let
    
```js
let one = '1';
let two = '2', three = '3';

console.info(one, two, three) // '1', '2', '3'

one = '01';

console.info(one, two, three) // '01', '2', '3' 
```

## Шаблонные строки
```js
    const a = 1;
    const b = 2;
    const total = 'Total'
    `${total}: ${a} + ${b}`
    
    `${foo()}` // Можно вызвать функцию

    `Многострочная 
      запись`
```
    
## Параметры функций по умолчанию
```js
    const x = 3;
    const sum = function (x, y = 10) {
        return x + y;
    }
```
     
## Стрелочные функции
    - Стрелочная функция не имеет своего контекста
    - Нельзя использовать в качестве конструктора
```js
    const myFunction = () => {}
    const multiply = (left, right) => left * right // return left * right
```

## Деструктуризация массива 
```js

```

## Деструктуризация объекта    
```js

```    
    
## Проблемы ES5
    
1. **Подвешивание переменных** (hoisting) - механизм в JavaScript, в котором переменные и объявления функций, передвигаются вверх своей области 
    видимости перед тем, как код будет выполнен. Как следствие, это 
    означает то, что совершенно не важно где были объявлены функция или 
    переменные, все они передвигаются вверх своей области видимости, 
    вне зависимости от того локальная она или же глобальная.
    
```js
console.info(number); // undefined

number = 3; 
console.info(number) // 3

var number = 2; 
console.info(number) // 2
```    
      
2. Переопределение переменных через `var` 

```js
// Переопределение переменных через var
var number = 5;

var print = function () {
    console.log(number);
}

// Очень   
// длинный
// код

var number = 3;
print();

// Выведет 5, 3
```

3. Потеря окружения

```js
var elements = [
    document.createElement('a'),
    document.createElement('a')
]

for (var i = 0; i < elements.lengtn; i ++) {
    var double = i * 2;
    
    elements[i].onclick = function (evt) {
        evt.preventDefault();
    
        console.info(i + '* 2 =' + double);
    }
}

elements[0].click();
elements[1].click();

console.info(i);
console.info(double); 

// 2 * 2 = 2
// 2
```

    
