---
title: 자바스크립트 기본 정리 06 - 객체(Object)
date: 2018-10-30 17:57:55
tags:
---

## 객체 리터럴 (Object Literal)

- 객체는 한꺼번에 여러 값을 담을 수 있는 통과 같은 **자료구조(data structure)** 이다. 

- 객체 안에는 **이름-값 쌍(name-value pair)** 이 저장되는데 이를 객체의 **속성(property)** 라고 한다.


```javascript
const age = 3;
const howManyCute = 'awesome';
const toy = 'fishing'

const pets = {
  name : '비비',
  '털 색' : ['white', 'gray'], // 2.
  age : age, // 3.
  howManyCute, // 3.
  [toy] : 'devilSnake', // 4.

  greet : function(){ // 5.
    return 'HELLO!!'
  },

  introduce(){ // 7.
    return `I am ${this.name}. I AM ${this.howManyCute.toUpperCase()}` // 8.
  }

};

pets.name // '비비'
pets.age // 3
pets.fishing // 'devilSnake'
pets.greet() // 'HELLO!!'
pets.introduce() // 'I am 비비. I AM AWESOME'

/*
name, '털 색', age ... - 속성 이름
'비비', 3, 배열 ... - 속성 값
*/
```

1. 속성 이름 부분에 문자열을 사용해도 상관 없다.

1. `'털 색'` 과 같이 속성이름에 식별자에 허용되지 않는 문자(한글, 공백)가 들어간 경우 반드시 문자열 표기를 사용해야 한다.

1. 이미 정의된 변수의 이름을 그대로 속성의 값으로 사용할 수도 있다.(객체 속성 이름과 속성 값으로 넣을 변수의 이름이 같다면(howManyCute) 줄여 쓸 수 있다.)

1. 대괄호를 사용해서 다른 변수에 저장된 문자열을 그대로 속성의 이름으로 사용할 수 있다.

1. 객체의 속성값으로 함수를 지정할 수 있다. 

1. **어떤 객체의 속성으로 접근해서 사용하는 함수를 메소드(Method) 라고 한다**

1. 객체 리터럴 안에서 특별한 표기법을 사용해 메소드를 정의할 수도 있다.

1. `this` 키워드를 사용하면, 메소드 호출 시에 해당 메소드를 갖고 있는 객체에 접근할 수 있다.


## 점 표기법, 대괄호 표기법

```js
const pets = {}; // 빈 객체

// 점 표기법 (Dot notation)
pets.name = '비비';
pets.age = 3;

// 대괄호 표기법 (Bracket notation)
person['털 색'] = ['white', 'gray'];
```

1. **속성 접근자(property accessor)** 를 이용해 이미 생성된 객체의 속성을 지정해 줄 수 있다.

1. 식별자에 허용되지 않는 문자(한글, 공백)를 속성 이름에 넣어야 할 경우에는 반드시 **대괄호 표기법**을 사용해야 한다.


## 객체 다루기

```js
// 속성 삭제하기
delete pets.age;
  
// 속성이 객체에 존재하는지 확인하기
'age' in pets; // false : 위에서 삭제함
'털 색' in pets; // true
```

- 속성 접근자, `delete` 연산자, `in` 연산자 등을 이용해서 객체에 대한 정보를 읽고 쓸 수 있다.


## 메소드 (Method) - 위 예제


## This 
 
```js
function introduce(){
  return `제 이름은 ${this.name}이고 ${this.age}살 입니다.`
}

function getOlder(){
  this.age++
}

const bibi = {
  name : '비비',
  age : 3,
  introduce,
  getOlder,
}

const doong = {
  name : '둥둥',
  age : 1,
  introduce,
  getOlder,
}

// 3.
console.log(bibi.introduce()) // 제 이름은 비비이고 3살 입니다.
console.log(doong.introduce()) // 제 이름은 둥둥이고 1살 입니다.
bibi.getOlder()
console.log(bibi.introduce()) // 제 이름은 비비이고 4살 입니다.
bibi.getOlder()
console.log(bibi.introduce()) // 제 이름은 비비이고 5살 입니다.
bibi.getOlder()
console.log(bibi.introduce()) // 제 이름은 비비이고 6살 입니다.
console.log(doong.introduce()) // 제 이름은 둥둥이고 1살 입니다.
```

1. 메소드를 사용하면 **데이터** 와 그 데이터와 관련된 **동작** 을 **객체라는 하나의 단위로 묶어서 다룰 수 있다** . (함수 대신 메소드를 사용하는 핵심적인 이유)

1. `function` 키워드를 통해 정의된 함수 내부의 `this` 키워드는 **함수가 호출될 때 결정** 된다.

1. **어떤 객체의 메소드로 사용되느냐에 따라 메소드 내부의 `this`가 가리키는 객체가 달라질 수 있다**

1. 다만 **화살표 함수는 함수가 정의된 문맥에 따라 `this`가 결정된다** .


## 프로토타입 (Prototype)
    
- 객체 간에 공유되어야 하는 속성과 메소드를 프로토타입이라는 기능을 이용해서 저장한다.

- 어떤 객체에 프로토타입을 지정하면, 프로토타입의 속성을 해당 객체에서 **재사용** 할 수 있다.

```js
const petsPrototype = {
  introduce : function(){
    return `제 이름은 ${this.name} 입니다`;
  }
};

const bibi = Object.create(petsPrototype); // 새 객체를 생성하고 프로토타입을 지정함
bibi.name = '비비';

const doong = Object.create(petsPrototype);
doong.name = '둥둥';

bibi.introduce(); // 제 이름은 비비 입니다.
doong.introduce(); // 제 이름은 둥둥 입니다.

Object.getPrototypeOf(bibi) === petsPrototype // 6.

Object.setPrototypeOf(bibi, newPetsPrototype) // 7.
```

1. 프로토타입 기능을 이용해 한 객체에서 다른 객체의 기능을 가져와 사용하는 것을 **프로토타입 상속(prototype inheritance)** 라고 한다.

1. **`petsPrototype`은 `bibi`의 프로토타입이다.**

1. `petsPrototype`은 `doong`의 프로토타입이다.

1. **`bibi` 객체는 `petsPrototype` 객체를 상속받았다.**

1. `doong` 객체는 `petsPrototype` 객체를 상속받았다.

1. `Object.getPrototypeOf` 함수를 사용해 어떤 객체의 프로토타입을 읽어올 수 있다.

1. `Object.setPrototypeOf` 함수를 사용해 이미 생성된 객체의 프로토타입을 변경할 수 있다. (굉장히 느리므로 사용은 지양한다.)

