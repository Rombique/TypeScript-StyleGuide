
# TypeScript StyleGuide and Coding Conventions

О чем тут говорим:

* [Variable](#variable-and-function)
* [Class](#class)
* [Interface](#interface)
* [Type](#type)
* [Namespace](#namespace)
* [Enum](#enum)
* [`null` vs. `undefined`](#null-vs-undefined)
* [Formatting](#formatting)
* [Single vs. Double Quotes](#quotes)
* [Tabs vs. Spaces](#spaces)
* [Use semicolons](#semicolons)
* [Annotate Arrays as `Type[]`](#array)
* [File Names](#filename)
* [`type` vs `interface`](#type-vs-interface)

## Variable and Function
* Необходимо использовать `camelCase` для именования переменных и функций.

***Bad***
```ts
var FooVar;
function BarFunc() { }
```
***Good***
```ts
var fooVar;
function barFunc() { }
```

## Class
* Используй `PascalCase` для имен классов.

***Bad***
```ts
class foo { }
```
***Good***
```ts
class Foo { }
```
* Используй `camelCase` для членов класса и методов.

***Bad***
```ts
class Foo {
    Bar: number;
    Baz() { }
}
```
***Good***
```ts
class Foo {
    bar: number;
    baz() { }
}
```
## Interface

* Используй `IPascalCase` для именования.

* Используй `camelCase` для членов интерфейса.

* **Обязательно используй** префикс `I` 

* По возможности используй постфикс `able`

***Bad***
```ts
interface Foo {
}
```
***Good***
```ts
interface IFoo {
}
```
***Good***
```ts
interface IFooable {
}
```

## Type

* Используй `PascalCase` для именования.

* Используй `camelCase` для членов.

## Namespace

* Используй `PascalCase` для именования.

***Bad***
```ts
namespace foo {
}
```
***Good***
```ts
namespace Foo {
}
```

## Enum

* Используй `PascalCase` для именования.

***Bad***
```ts
enum color {
}
```
***Good***
```ts
enum Color {
}
```
* Используй `PascalCase` для члена перечисления.

***Bad***
```ts
enum Color {
    blue,
    yellow,
}
```
***Good***
```ts
enum Color {
    Blue,
    Yellow,
}
```

## Null vs. Undefined

* По возможности лучше не использовать неопределенные значения.

***Bad***
```ts
let foo = {x:12345,y:undefined,};
```
***Good***
```ts
let foo:{x:number,y?:number,} = {x:12345};
```

* Если используешь неопределенные значения то старайся возвращать `undefined` в большинстве случаев.

***Bad***
```ts
return null;
```
***Good***
```ts
return undefined;
```

* Используй`null` только тогда, когда это необходимо (например это предусмотрено API).

***Bad***
```ts
callback(undefined)
```
***Good***
```ts
callback(null)
```

* Используйте упрощенную проверку объектов которые могут быть `null` или `undefined`

***Bad***
```ts
if (error === null)
```
***Good***
```ts
if (error)
```

* Используйте `== undefined` / `!= undefined` (не `===` / `!==`) для проверки на `null` / `undefined`.  В случае если произойдет ситуация когда в переменной будет что-то вроде  `''`,`0`,`false`, `'undefined'` и т.д. все будет обработано корректно.

***Bad***
```ts
if (error !== null)
```
***Good***
```ts
if (error != undefined)
```

## Quotes

* Используй одинарные кавычки (`'`).

## Formatting

* Всегда ставь запятые после каждого перечисления.

***Bad***
```ts
const object = {
	propertyOne: 1,
	properyTwo: 'two'
};
```
***Good***
```ts
const object = {
	propertyOne: 1,
	properyTwo: 'two',
};
```

## Spaces

* Используй `2` пробела. Не используй табы.

## Semicolons

* Используй точку с запятой в конце каждого выражения.

## Array

* Инициализируй массив с помощью аннотации вида `foos:Foo[]`, а не `foos:Array<Foo>`.

## Filename
Имена обычных файлов должны быть в  `camelCase`. Например, `main.ts`, `stringUtils.ts`, `mapReduce.ts`. Имена файлов классов должны быть в `PascalCase`. Например, `SPUserRepository.ts`, `SPUserProvider.ts`.

## type vs. interface

* Используй `type` когда может понадобиться пересечение или объединение:
```
type Foo = number | { property: number }
```
* Используй `interface` если в будущем будешь расширять (`extends`) или реализовывать (`implements`) интерфейс.

```ts
interface Foo {
  foo: string;
}
interface FooBar extends Foo {
  bar: string;
}
class Baz implements FooBar {
  foo: string;
  bar: string;
}
```
