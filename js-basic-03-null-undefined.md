---
title: 자바스크립트 기본 정리 03 - Null, Undefined
date: 2018-10-23 15:38:11
tags:
---

1. `null` 
- `없음`을 나타내는 값
- `객체가 없음`을 나타낸다.
- `typeof` 연산을 해보면 아래와 같은 값을 반환한다.

```javascript
typeof null // 'object'
typeof undefined // 'undefined'
```

1. `undefined`
- `없음`을 나타내는 값
- 값이 대입되지 않은 변수 혹은 속성을 사용하려고 하면 `undefined`를 반환한다.

```javascript
let foo;
foo // undefined => 값이 대입되지 않음.

const obj = {};
obj.prop // undefined
```

1. 프로그래머의 입장에서 명시적으로 부재를 나타내고 싶다면 항상 `null`을 사용하는 것이 좋다.

1. 객체를 사용할 때 어떤 속성의 부재를 나타낼 때에는 `null`보다는, 아예 속성을 정의하지 않는 방식이 간편하므로 더 널리 사용된다.

```javascript
// null로 정의하는 법
{
    name : 'bibi',
    address : null
}

// 속성을 정의하지 않는 법
{
    name : 'bibi'
}
```

1. Null Check

-`null`이나 `undefined`는 어떤 변수에도, 어떤 속성에도 들어있을 수 있기 때문에 코드를 짤 때 값이 있는 경우와 값이 없는 경우(즉 `null` 혹은 `undefined`인 경우)를 모두 고려해서 짜야한다. 
- 어떤 값이 `null` 혹은 `undefined` 인지 확인하는 작업을 **null check** 라고 한다.

```javascript
function printIfNotNull(input){
    if(input !== null && input !== undefined){
        console.log(input);
    }
}
```

- 위 코드를 줄일 수 있다

```javascript
// 아래의 세 식은 같은 의미이다.
input !== null && input !== undefined
input != null
input != undefined


// 아래의 세 식은 같은 의미이다.
input === null || input === undefined
input == null
input == undefined
```

- null check를 할 때에는 `===` 보다는 `==`를 사용한다

```javascript
null === undefined // false
null == undefined // true

null == 1 // false
null == 'hello' //false
null == false // false

undefined == 1 // false
undefined == 'hello' // false
undefined == false // false
```

- `==` 연산자는 한 쪽 피연산자에 `null`  혹은 `undefined`가 오면, 다른 쪽 피연산자에 `null` 혹은 `undefined`가 왔을때만 `true`를 반환하고, 다른 모든 경우에는 `false`를 반환한다.
