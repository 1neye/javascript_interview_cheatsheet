# Шпаргалка по Javascript

Здесь собраны часто встречающиеся вопросы на собеседовании по Javascript.

---

## **База**
<details>
<summary>Назови типы данных в Js </summary>
    <div>Null, undefined, number, string, bolean, object, bigint, symbol</div>
</details>
    
<details>
<summary> Чем отличается let var и const </summary>
    <div>
    <p>Переменная, объявленная через <code>var</code>, видна везде в функции.</p>
    <p>Переменная, объявленная через <code>const</code> или <code>let</code>, видна только в рамках блока <code>{...}</code>, в котором объявлена.</p>
    <p>Объявление <code>const</code> задаёт константу, то есть переменную, которую нельзя менять:</p>
    <p>

```jsx
    const apple = 5;
    apple = 10; // ошибка
```
  </p>
</div>
</details>
    <details>
<summary>Чем отличается == от ===</summary>
    <div>
    <p>== и === это операторы который проверяют равны ли операнды и возвращает bolean true или false</p>
    <p>== проверяет равны ли операнды даже если они разных типов</p>
    <p>=== строгое равенство которое проверяет равны ли не только операнды но и их типы</p>
</div>
</details>
    <details>
<summary>Чем отличается setTimeout от setInterval</summary>
    <div>
    <p><code>setTimeout</code> позволяет вызвать функцию **один раз** через определённый интервал времени.</p>
    <p><code>setInterval</code> позволяет вызывать функцию **регулярно**, повторяя вызов через определённый интервал времени.</p>

</div>
</details>
    
<details>
<summary>Что такое use strict</summary>
<div>
    <p>[use strict](https://learn.javascript.ru/strict-mode) - это установка, которая заставляет код обрабатываться в *строгом режиме*. Без этой установки код обрабатывается в *неограниченном режиме*. Это установку нужно писать в начале файла.</p>
    <p>Строгий режим ограничивает функционал javascript в пользу багоустойчивого кода.</p>
    <p>Например:</p>
    <p>Нельзя присваивать значение в неопределённую переменную</p>
<p>

```jsx
    (function() {
      "use strict";
      x = 5; // ReferenceError: x is not defined
    })();
    
    x = 5; // Создает глобальную переменную x
```

</p>
    
<p>Нельзя дублировать свойства обьекта</p>
    
<p>

```jsx
    (function() {
      "use strict";
      var x = {
        a: 1,
        a: 2
      };  // SyntaxError: Duplicate data property in object literal
    })(); // not allowed in strict mode
    
    var x = {
      a: 1,
      a: 2
    }; // x равно {a: 2}
```

</p>
</div>
</details>

<details>
<summary>Что такое Callback</summary>
<div>
    <p>Коллбэк — это функция, которая должна быть выполнена после того, как другая функция завершила выполнение</p>
</div>
</details>

## **Объекты**
<details>
<summary>Перечисли методы объекта</summary>
<div>
<ul>
    <li>Object.create()</li>
    <li>Object.keys()</li>
    <li>Object.values()</li>
    <li>Object.entries()</li>
    <li>Object.assign()</li>
    <li>Object.freeze()</li>
    <li>Object.seal()</li>
    <li>Object.getPrototypeOf()</li>
</ul>
  </div>
</details>
<details>
<summary>Что такое глубокое и неглубокое копирования</summary>
<div>
    <p>При копировании объектов или массивов JavaScript копирует данные только на один уровень вглубь. Этот тип копирования называется поверхностным (shallow). Если необходимо полностью скопировать сложную структуру данных, например, массив с объектами, то нужно делать глубокое (deep) или полное копирование данных.</p>
    
<p>

```jsx
    const itemsInCart = [
      { product: 'Носки', quantity: 3 },
      { product: 'Штаны', quantity: 1 },
      { product: 'Кепка', quantity: 1 },
    ]
    
    const clonedCart = [...itemsInCart]
 ```

 </p>

 <p>
    
```jsx
    const deep = JSON.parse(JSON.stringify(itemsInCart))
    console.log(itemsInCart[1] === deep[1])
    // false
```

</p>
    
<p>У этого метода есть ограничение — копируемые данные должны быть сериализуемы.</p>

<p>
Вот примеры несериализуемых данных: примитив undefined, функция, [symbol](https://doka.guide/js/symbol/) - при вызове JSON.stringify получаем undefined
</p>    


</div>
</details>

<details>
<summary>Как удалить значение объекта</summary>
<div>

   <p> С помощью оператора <code>delete</code></p>

</div>
</details>

    
<details>
<summary>Что такое деструктуризация?</summary>
<div>
<p>[Деструктуризация](https://learn.javascript.ru/destructuring) - это особый синтаксис, позволяющий извлекать значения из объектов</p>
</div>
</details>
    
<details>
<summary>Деструктуризируй объект</summary>
<div>

```jsx
    const objToDestr = {
      name: 'John',
      age: 20,
      address: {
        country: 'Ukraine',
        city: 'Kyiv'
      },
    }
    
    let {name, address: {country}} = objToDestr
    console.log(name, country)
```

</div>
</details>

<details>
<summary>Что такое new Map</summary>
<div>
    <p>[Map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map) – это коллекция ключ/значение, как и `Object`. Но основное отличие в том, что `Map` позволяет использовать ключи любого типа.</p>
</div>
</details>

<details>
<summary>Что такое weakMap</summary>
<div>
    weakMap - это тоже самое что и Map только более оптимизированно.
</div>
</details>

<details>
<summary>Расскажи что такое this</summary>
<div>
    
<p>Для доступа к информации внутри объекта метод может использовать ключевое слово <code>this</code></p>
<p>This — это ключевое слово, используемое в JavaScript, которое имеет особое значение, зависящее от контекста в котором оно применяется</p>
    
```jsx
    let user = {
      name: "John",
      age: 30,
    
      sayHi() {
        // "this" - это "текущий объект".
        alert(this.name);
      }
    
    };
 ```
</div>
</details>

<details>
<summary>Как работают методы apply(), call() и bind()</summary>
<div>
    
Функции в JavaScript никак не привязаны к своему контексту this, с одной стороны, здорово – это позволяет быть максимально гибкими, одалживать методы и так далее.
    
Но с другой стороны – в некоторых случаях контекст может быть потерян. Способы явно указать this - методы bind, call и apply.
    
- Синтаксис метода call: func.call(context, arg1, arg2, ...)
        
При этом вызывается функция func, первый аргумент call становится её this, а остальные передаются «как есть». Вызов func.call(context, a, b...) – то же, что обычный вызов func(a, b...), но с явно указанным this(=context).
        
- Если нам неизвестно, с каким количеством аргументов понадобится вызвать функцию, можно использовать более мощный метод: apply. Вызов функции при помощи func.apply работает аналогично func.call, но принимает массив аргументов вместо списка.
        
func.call(context, arg1, arg2) идентичен вызову func.apply(context, [arg1, arg2]);
        
- Синтаксис встроенного bind: var wrapper = func.bind(context, [arg1, arg2...])
        
Методы bind и call/apply близки по синтаксису, но есть важнейшее отличие. Методы call/apply вызывают функцию с заданным контекстом и аргументами. А bind не вызывает функцию. Он только возвращает «обёртку», которую мы можем вызвать позже, и которая передаст вызов в исходную функцию, с привязанным контекстом.
        
    
*Источник: [javascript.ru - call и apply](https://learn.javascript.ru/call-apply#metod-apply) [javascript.ru - bind](https://learn.javascript.ru/bind#bind)*

</div>
</details>
    
## **Массивы**
 
<details>
<summary>Какие методы массивов ты знаешь</summary>
<div>
Шпаргалка по методам массива:
    
- Для добавления/удаления элементов:
        - `push (...items)` – добавляет элементы в конец,
        - `pop()` – извлекает элемент с конца,
        - `shift()` – извлекает элемент с начала,
        - `unshift(...items)` – добавляет элементы в начало.
        - `splice(pos, deleteCount, ...items)` – начиная с индекса `pos` удаляет `deleteCount` элементов и вставляет `items`.
        - `slice(start, end)` – создаёт новый массив, копируя в него элементы с индекса `start` до `end` (не включая `end`).
        - `concat(...items)` – возвращает новый массив: копирует все члены текущего массива и добавляет к нему `items`. Если какой-то из `items` является массивом, тогда берутся его элементы.
    - Для поиска среди элементов:
        - `indexOf/lastIndexOf(item, pos)` – ищет `item`, начиная с позиции `pos`, и возвращает его индекс или `1`, если ничего не найдено.
        - `includes(value)` – возвращает `true`, если в массиве имеется элемент `value`, в противном случае `false`.
        - `find/filter(func)` – фильтрует элементы через функцию и отдаёт первое/все значения, при прохождении которых через функцию возвращается `true`.
        - `findIndex` похож на `find`, но возвращает индекс вместо значения.
    - Для перебора элементов:
        - `forEach(func)` – вызывает `func` для каждого элемента. Ничего не возвращает.
    - Для преобразования массива:
        - `map(func)` – создаёт новый массив из результатов вызова `func` для каждого элемента.
        - `sort(func)` – сортирует массив «на месте», а потом возвращает его.
        - `reverse()` – «на месте» меняет порядок следования элементов на противоположный и возвращает изменённый массив.
        - `split/join` – преобразует строку в массив и обратно.
        - `reduce/reduceRight(func, initial)` – вычисляет одно значение на основе всего массива, вызывая `func` для каждого элемента и передавая промежуточный результат между вызовами.
    - Дополнительно:
        - `Array.isArray(arr)` проверяет, является ли `arr` массивом.

</div>
</details>
<details>
<summary>Чем отличается map от forEach</summary>
<div>

1.  map сохраняет значение через return, forEach всегда возвращает undefined 
2. Второе различие между этими методами: map() можно привязывать к другим методам - reduce(), sort(), filter() и т.д. А вот forEach(), как вы можете догадаться, возвращается undefined.
2. map более производительный
3. map относится к функциональному программированию, а forEach к процедурному

</div>
</details>

<details>
<summary>Расскажи про reduce</summary>
<div>
    
Reduce используется для последовательной обработки каждого элемента массива с сохранением промежуточного результата.
    
```jsx
    let arr = [1, 2, 3, 4, 5]
    
    var result = arr.reduce(function(sum, current) {
    return sum + current;
    }, 0);
    
    alert( result ); // 15
    
    //sum результат добавления двух чисел в начале 
    //берет значение 2 аргумента или 1 элемента массива
    //current текущее значение массива которая в цикле меняеться 1,2,3...
    // цикл будет выполняться следующим образом
    // 0 + 1
    // 1 + 2
    // 3 + 3
    //...
    
```

</div>
</details>

<details>
<summary>Что такое new Set</summary>
<div>
    
Set – это коллекция как и `Array`. Но основное отличие в том, что в Set каждое значение может появляться только один раз.

</div>
</details>

<details>
<summary>Что такое weakSet</summary>
<div>
    
weakSet - это тоже самое что и Set только более оптимизировано.
    
</div>
</details>

## **Продвинутый**

<details>
<summary>Расскажи про Promise</summary>
<div>
    
[Promise](https://learn.javascript.ru/promise) — специальный объект JavaScript, который используется для написания и обработки асинхронного кода например запросов  с сервера
    
Способ использования, в общих чертах, такой:
    
1. Код, которому надо сделать что-то асинхронно, создаёт объект `promise` и возвращает его.
2. Внешний код, получив `promise`, навешивает на него обработчики.
3. По завершении процесса асинхронный код переводит `promise` в состояние `fulfilled` (с результатом) или `rejected` (с ошибкой). При этом автоматически вызываются соответствующие обработчики во внешнем коде.
    
Синтаксис создания `Promise`:
    
```jsx
    let promise = new Promise(function(resolve, reject) {
      // Эта функция будет вызвана автоматически
    
      // В ней можно делать любые асинхронные операции,
      // А когда они завершатся — нужно вызвать одно из:
      // resolve(результат) при успешном выполнении
      // reject(ошибка) при ошибке
    })
```

</div>
</details>

<details>
<summary>Чем отличаются стрелочные функции от обычной функции</summary>
<div>
    
[Стрелочные функции](https://learn.javascript.ru/arrow-functions):
    
- Сокращают написание функции
- Не имеют `this`.
- Не имеют `arguments`.
- Не могут быть вызваны с `new`.

</div>
</details>

<details>
<summary>Что такое Event Loop и как он устроен</summary>
<div>
Event Loop - это бесконечный цикл событий, благодаря которому мы можем реализовать многопоточность в javascript. 

<p></p>
    
Многопоточность - это способность выполнять несколько параллельных задач - потоков

</div>
</details>

<details>
<summary>Что такое рекурсия? И какое главное правило рекурсии?</summary>
<div>

Рекурсия в javascript это когда функция вызывает саму себя. Главное правило рекурсии это написать выход из нее.

</div>
</details>

<details>
<summary>Что такое замыкание</summary>
<div>
    
[Замыкание](https://learn.javascript.ru/closure) – это функция, которая запоминает свои внешние переменные и может получить к ним доступ. В некоторых языках это невозможно, или функция должна быть написана специальным образом, чтобы получилось замыкание. Но, как было описано выше, в JavaScript, все функции изначально являются замыканиями

</div>
</details>

<details>
<summary>Зачем нужны тесты</summary>
<div>
    
Тесты нужны для: 
    
1) Уменьшение количество багов
    
2) Уменьшение времени работы над таской. Чем больше тестов, тем более багоустойчив код. Тем меньше таска переходит от разработчика ⇒ тестировщику ⇒ менеджеру
    
3) хорошие тесты - это еще и документация, и они помогают быстрее адаптироваться новым членам команды

</div>
</details>

<details>
<summary>Что такое TDD</summary>
<div>
    
TDD - это аббревиату́ра которая означает Test-driven development. 

TDD - разработка на основе тестов.

</div>
</details>
    
<details>
<summary>Что такое BABEl</summary>
<div>
    
Babel - это транспайлер, который переписывает код современного стандарта Javascript (ES2015) на более поздний. Благодаря этому мы можем поддерживать браузеры которые не поддерживают новый функционал JS

</div>
</details>

<details>
<summary>Расскажи что такое ООП и методы этой парадигмы</summary>
<div>
    
Объектно-ориентированное программирование (в дальнейшем ООП) — парадигма программирования, в которой основными концепциями являются понятия объектов и классов.
    
**Абстрагирование** — это способ выделить набор значимых характеристик объекта, исключая из рассмотрения не значимые  Соответственно, абстракция — это набор всех таких характеристик.
    
**Инкапсуляция** — это свойство системы, позволяющее объединить данные и методы, работающие с ними в классе, и скрыть детали реализации от пользователя.
    
**Наследование** — это свойство системы, позволяющее описать новый класс на основе уже существующего с частично или полностью заимствующейся функциональностью. Класс, от которого производится наследование, называется базовым, родительским или суперклассом. Новый класс — потомком, наследником или производным классом
    
**Полиморфизм** — это свойство системы использовать объекты с одинаковым интерфейсом без информации о типе и внутренней структуре объекта.
    
[Источник](https://devcolibri.com/%D1%87%D1%82%D0%BE-%D1%82%D0%B0%D0%BA%D0%BE%D0%B5-%D0%BE%D0%BE%D0%BF-%D0%B8-%D1%81-%D1%87%D0%B5%D0%BC-%D0%B5%D0%B3%D0%BE-%D0%B5%D0%B4%D1%8F%D1%82/)

</div>
</details>

<details>
<summary>Чем отличается Функционально программирование от ООП</summary>
<div>

В объектно-ориентированном программировании (ООП) вы создаете «объекты» (отсюда и название), которые представляют собой структуры, содержащие данные и методы. В функциональном программировании все является функцией. Функциональное программирование пытается разделить данные и поведение, а ООП объединяет эти концепции.

</div>
</details>
    
<h2><strong>Другое</strong></h2>

<details>
<summary>0.1 + 0.2 в javascript что будет</summary>
<div>
    
Внутри JavaScript число представлено в виде 64-битного формата [IEEE-754](https://ru.wikipedia.org/wiki/IEEE_754-1985). Для хранения числа используется 64 бита: 52 из них используется для хранения цифр, 11 для хранения положения десятичной точки и один бит отведён на хранение знака.
    
Если число слишком большое, оно переполнит 64-битное хранилище, JavaScript вернёт бесконечность:
    
`alert( 1e500 ); // Infinity`
    
[Так что если 52 бит не хватает на цифры, то при записи происходит такой баг](https://learn.javascript.ru/number#:~:text=%D0%92%20JavaScript%20%D0%BD%D0%B5%D1%82%20%D0%B2%D0%BE%D0%B7%D0%BC%D0%BE%D0%B6%D0%BD%D0%BE%D1%81%D1%82%D0%B8%20%D0%B4%D0%BB%D1%8F,%D1%82%D1%80%D0%B5%D1%82%D1%8C%D1%8E%20%D0%B2%20%D0%B4%D0%B5%D1%81%D1%8F%D1%82%D0%B8%D1%87%D0%BD%D0%BE%D0%B9%20%D1%81%D0%B8%D1%81%D1%82%D0%B5%D0%BC%D0%B5%20%D1%81%D1%87%D0%B8%D1%81%D0%BB%D0%B5%D0%BD%D0%B8%D1%8F.) 
    
Для точных вычислений использую библиотеку [decimal.js](https://github.com/MikeMcl/decimal.js#readme)

</div>
</details>
    
<details>
<summary>Операции с разными типами в например true + true = ?</summary>
<div>

```jsx
    null + undefined = Nan
    null + {} = 'null[object Object]'
    null + [] = 'null'
    null + true = 1
    null - true = -1
    null + false = 0
    null - false = 0
    null + '' = 'null'
    
    true + true = 2
    true - true = 0
    true + false = 1
    true - false = 1
    true + undefined = Nan
    true + [] = 'true'
    true + {} = 'true[object Object]'
    true + '' = 'true'
    
    false - false = 0
    false + false = 0
    false + undefined = NaN
    false + [] = 'false'
    false + {} = 'false[object Object]'
    false + '' = 'false'
```
</div>
</details>

<details>
<summary>obj[0] + obj[’0’]</summary>
<div>
    
```jsx
    let obj = { 
    ”0”: 1,
    0: 2
    }
    obj[’0’] // 2 
    obj[0] // 2 
    
    console.log(obj[0] + obj[’0’]) //Будет ровно 4
```

</div>
</details>

<details>
<summary>Расскажи про requestAnimationFrame</summary>
<div>


</div>
</details>