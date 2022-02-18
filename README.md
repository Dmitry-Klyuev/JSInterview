# JavaScript собес Вопросы и ответы
| №   | Вопрос                                      |
|-----|---------------------------------------------|
| 1   | [В чем разница между null и undefined?](#1) |
| 2   | [Для чего используется оператор "&&"?](#2)  |

###1 В чем разница между null и undefined?

Для начала давайте поговорим о том, что у них общего.

Во-первых, они принадлежат к 7 «примитивам» (примитивным типам) JS:

```javascript
let primitiveTypes = ['string', 'number', 'null', 'undefined', 'boolean', 'symbol', 'bigint']
```
Во-вторых, они являются ложными значениями, т.е. результатом их преобразования в логическое значение с помощью Boolean() или оператора "!!" является false:
```javascript
console.log(!!null) // false
console.log(!!undefined) // false

console.log(Boolean(null)) // false
console.log(Boolean(undefined)) // false
```
Ладно, теперь о различиях.

undefined («неопределенный») представляет собой значение по умолчанию:
переменной, которой не было присвоено значения, т.е. объявленной, но не инициализированной переменной;
функции, которая ничего не возвращает явно, например, console.log(1);
несуществующего свойства объекта.

В указанных случаях движок JS присваивает значение undefined.
```javascript
let _thisIsUndefined
const doNothing = () => {}
const someObj = {
    a: 'ay',
    b: 'bee',
    c: 'si'
}
console.log(_thisIsUndefined) // undefined
console.log(doNothing()) // undefined
console.log(someObj['d']) // undefined
```
null — это «значение отсутствия значения». null — это значение, которое присваивается переменной явно. В примере ниже мы получаем null, когда метод fs.readFile отрабатывает без ошибок:
```javascript
fs.readFile('path/to/file', (e, data) => {
    console.log(e) // здесь мы получаем null
if(e) {
    console.log(e)
}
    console.log(data)
})
```
При сравнении null и undefined мы получаем true, когда используем оператор "==", и false при использовании оператора "===".
```javascript
console.log(null == undefined) // true
console.log(null === undefined) // false
```

###2 Для чего используется оператор "&&"?
