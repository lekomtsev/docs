## Структуры данных

```js
    // кратко охарактеризовать
```
## Проектирование структуры
    
    - выделить отдельные сущности
    - выявить свойства и методы сущностей и подобрать оптимальную структуру для каждой из них 
    - определиться, как сущности связаны между собой

    Варианты проектирования структуры: 
    - от общего к частному (с высока на что-то) или индуктивный метод
    - от частного к общему или дедуктивный метод

    * Список - (последовательность) упорядоченный набор значений, в котором 
        одно значение может встречаться более одного раза (пример Array)
    * Множество - набор уникальных значений, без определнного порядка (пример Set, WeakSet)
    * Словарь - (ассоциативный массив) структура данных, которая используется для соспоставления одних значений другим.
        Представляет собой набор пар "ключ, значение" (пример Object, Map, WeakMap)

## Работа с объектами

```js
    const students = {
        firstName: 'John',
        lastName: 'Dow',
        age: 21
    }
    
    // Получаем массив пар ключ,значение
    const keys = Object.entries(students) // ['fistName', 'John']

    // Получаем массив значения 
    const values = Object.values(students) // ['John', 'Dow', 21]

    // Получаем массив ключей
    const keys = Object.keys(students) // ['fistName', 'lastName', 'age']

    for (const propertyName of keys) {
        // Перебираем все ключи объекта
        if (typeof students[propertyName] === `function`) {
            students[propertyName]()
        }
    }

    for (const key in students) {
        if (typeof students[key] === `function`) {
            students[key]()
        }
    }
    
    // Удаление свойства
    delete students.age

    // Проверка на существование свойства
    // 1) Сравнить с undefined
    (students.firstName !== undefined)
        
    // 2) Воспользоваться оператором in - более надежный
    (`firstName` in students)

    // 3) hasOwnProperty
    (students.hasOwnProperty('firstName'))

    // Getter
    const car = {
        get brand() {
            return 'Message'
        }        
    }
    // Обращаемся как обычному свойству объекта car.brand

    // Setter
    const car = {
        set brand(newName) {
            this.name = newName
        }
    }
    // car.brand = 'Ford'

```

## [Работа с массивами](https://codepen.io/mclaren/pen/BaLLzyp)

    - sort - cортировка, изменяет существующий массив! (нужно использовать slice())
    - filter - фильтрация 
    - slice(с какого индекса берем, по какой индекс = если пусто то берет до конца массива) - взять часть массива 
    - map - преобразовать один массив в другой
    - reduce - помогает делать преобразования
    - find - найдет первый элемент и остановится

    * Стек - последний пришедший в стек уходит из него первым (пример история браузера)
    * Очередь - последний пришедший уходит последним
    
```js
    // rest - собирает из аргументов массив (используется в аргументах фукнций)
    const names = ['John', 'Alex', 'Mike'] 
    (name, ...title)
        
    // spread - разбирает массив на аргументы (используется везде кроме аргументов функций)
    (...names) // передастся 3 аргумента
```


    
    
    
 
