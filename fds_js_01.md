# 2018-09-27 자바스크립트 1 일차

## 객체

- property
- 정해진 순서가 없음.

```js
const obj = {
  x: 0,
  y: 1
};
```

`>> 객체 리터럴에는 속성 리터럴 두 쌍이 들어있다..`

- 속성 안에는 뭐든지 들어갈 수 있다. 함수도 가능

```js
//객체 안에 객체를 저장하는 경우
const obj =
  {
    x: "best",
    y: {
      x: 1,
      y: 2
    }
  } >> obj.y.x;
```

-

```js
const obj = {
  x: 0,
  increaseX: function() {
    this.x = this.x + 1;
  }
};

obj.increaseX();
// 어떤 객체의 메소드 안에 this가 있으면
// 그 this는 '메소드가 호출될 때' 해당 객체를 가리키게 된다.
console.log(obj.x); // 1
```

## 배열

- 정해진 순서가 있고 순서를 따라야 한다.
- 배열 안에 뭐든지 넣을 수 있다.
  - 배열 안의 배열, 배열 안의 객체, 배열 안의 문자열, 숫자, 등...

```js
const arr = [1, 2, 3]; //배열의 선언
arr.push(4); // 배열 추가
arr.push(5);

arr.splice(2, 3); // 배열 삭제. 2번배열부터 3자리의 배열을 지운다. (배열은 0부터)
```

## 2.1 값 다루기

- 리터럴은 표기법 값은 정보
- 특별한 일을 하는 단어를 키워드라고 한다 : let, while, for, if ...
- best practice : 좋은 관례 (ex. var 대신에 let 을 쓴다)
- `const`는 재대입이 불가능해서 선언과 대입을 동시에 해주어야 한다

```js
const a = 0;
```

- `let`은 재대입이 가능하기때문에 선언과 대입을 따로 해도 된다.

```js
let a;
a = 1;
a = 2;
```

## 넘버타입

## 증감 연산자

- `a++` 1 증가시키기 전 값을 표현식의 결과값으로 반환
- `++a` 1 증가시킨 후의 값을 표현식의 결과값으로 반환

## 부동 소수점, 고정 소수점

## NaN

- 어떤 값이 NaN 인지 아닌지를 판별하고 싶을때는 등호를 쓰면 안된다

```js
a === NaN; // 이 등호들은 숫자에 특화된 등호들.
a !== NaN;
```

- `"NaN은 숫자가 아니기 때문에, 어떤 숫자와도 같지 않다."` 라는 규칙이 있다.
- 즉, NaN 은 number 타입인 NaN 과 같지 않다.
- `===NaN` 은 무조건 false 가 나오는 식이다.

## -0

- `Object.is(0,-0)` 실제로 자바스크립트 세계에서 같은 값인지?

```js
Math.floor(Math.random() * 6 +1 //주사위를 만드는 법
```

```js
const CARDS = ["A", "b", "C"];

CARDS[Math.floor(Math.random() * 3)];
// 세가지 카드 중 하나만 랜덤으로 고른다.
```

# 2018-09-28 자바스크립트 2 일차

## String 타입

### 문자열 리터럴

- 따옴표 안에는 다른 종류의 따옴표를 넣을 수 있다.
  - ex, 'my name is "soyoung"'

### 템플릿 리터럴

- 내삽(interpolation) 기능

```js
const name1 = "Foo";
const name2 = "Bar";
const sentence = `${name1} meets ${name2}!`;
console.log(sentence);

// 일반적인 문자열 리터럴로는 아래와 같이 해야 합니다.
name1 + " meets " + name2 + "!";
```

- 여러줄로 이루어진 문자열 표현

```js
`hello
world
hello
javascript!
`;

// 일반적인 문자열 리터럴로는 아래와 같이 해야 합니다.
("hello\nworld\nhello\njavascript!\n");
```

- 특이한 형태의 함수 호출 기능
  - 어려움

### Escape Sequence

- `\n` `\r` : 개행문자(엔터, 줄바꿈)
  - 운영체제마다 엔터를 쳤을 때 입력되는 문자가 다르다.
  - 보통 웹에선 `\n`을 사용

### 유니코드 사이트

[재밌는 유니코드](http://graphemica.com)

### 문자열과 연산자

- 문자열 연결하기

```js
"number" + 1 + 3;
("number13");
// 왼쪽부터 number와 1이 먼저 계산되고, 결과는 문자열로 출력이 된다. ('number1')
// 이 문자열에 다시 3이 더해진다.
```

- 등호 비교
  - 부등호로 문자열을 비교하면 사전순 비교`(a < z)`가 아니기 때문에 원하는 값이 나오지 않을 수 있다.

```js
"a" < "b"; //true b의 코드포인트가 더 크다.
"a" > "Z"; // true 대문자Z보다 소문자a의 코드포인트가 크다.
```

- 문자열을 배열로 바꾸기

```js
[..."hello"]; //['h', 'e', 'l', 'l', 'o']

// 또는

"hello".split("");
```

### 속성 및 메소드

```js
"hello javascript".includes("hello"); // true 왼쪽문자열에 hello가 포함되어있는지

"hello javascript".startsWith("he"); // true 'he'라는 문자열로 시작하고있는지

"hello javascript".indexOf("java"); // 6 java라는 문자열이 몇번째에 있는지? 0부터 시작해서 공백도 포함

"hello javascript".indexOf("python"); // -1 포함되어있지 않은 문자열이 나왔을때는 -1 출력
```

```js
"hello javascript".replace("hello", "bye"); // 'bye javascript'
```

```js
// 문자열의 일부를 잘라낸 새 문자열 생성하기
"hello".slice(2, 4); // 'll'
// 문자열의 틈마다 번호를 매긴다.
// [0]h[1]e[2]l[3]l[4]o[5]
```

- `.slice`, `.trim`, `.trimLeft`, `.trimRight` 메소드는 원본 문자열을 변경하지 않는다.

- split

```js
"sovv@gmail.com".split("@")[0]; // sovv
"sovv@gmail.com@sot@may".split(".com")[0]; // 'sovv@gmail'
```

- 모든 문자를 대문자 혹은 소문자로 변환
  - 보통 검색결과를 보여줄 때 사용. -사용자가 소문자로 검색해도 대문자 검색결과까지 표출될 수 있게.
  - 검색한 내용을 모두 대문자로 변경 후 검색 진행

```js
"Hello JavaScript".toLowerCase(); // 'hello javascript'
"Hello JavaScript".toUpperCase(); // 'HELLO JAVASCRIPT'
```

### 외전. UTF-8 과 UTF-16

- UTF-8 : 글자를 1~4 바이트로 변환하여 인코딩한다 = 알파벳같은 경우에는 1 바이트로 용량이 적다. / 인코딩하는데 시간이 걸린다.
- UTF-16 : 글자를 그대로 유지하여 최소 16 비트( 2 바이트)에서 32 비트(4 바이트)로 인코딩한다 = 알파벳도 2 바이트부터 시작해 용량이 클 수 있다. / 문자를 그대로 가져가기 때문에 변환에 시간이 걸리지 않는다.

## boolean 불리언 타입

- true, false 두가지 밖에 없다.

### 논리연산자

- 중요! 모두 알아야 함.
- 삼항연산자
  - 특정 조건을 만족할 때 어떤 결과값을 바로 반환하고 싶을 때는 삼항연산자를 사용
  - if 와 비슷하게 동작함
  - if 는 표현식이 아니지만 삼항연산자는 표현식이다.

```js
// 특정 조건을 만족할 때 바로 결과값을 반환하고 싶은 경우
const result = true ? 1 : 2;

// 특정 조건을 만족할 때 여러 명령을 실행하고 싶은 경우
```

### 연산자 우선순의

확인 필요

### 논리 연산의 여러 가지 법칙

- 복잡한 조건식을 만들 때엔 조건표를 그려서 확인해라

```
a|b
T|T
T|F
F|T
F|F
```

### truthy & falsy

- boolean 값이 아니더라도 true 와 false 값으로 취급되는 값이 있다.
- true 로 취급되는 값 truthy
- false 로 취급되는 값 falsy ★
  - false
  - null
  - undefined
  - 0
  - NaN
  - '' (빈 문자열)
- falsy 를 제외한 모든 값들은 truthy ★
  - 숫자
  - 객체
  - 배열
  - 함수

```js
const input = prompt("이름이 무엇인가요?")

if (input.length > 0){
  alert(`안녕하세요 ${input}님`)
}else{
  alert('이름을 입력해주세요')
}

//input.length > 0 은 input만 적을 수도 있다. truthy와 falsy의 성질을 이용해서.
// 0값은 무조건 false이니 ..

if(input){
  ~
}
```

### 다른 타입의 값을 진리값으로 변환하기

- truthy 인 값을 진짜 true 로 바꾸고 싶을 때,
  falsy 인 값을 진짜 false 로 바꾸고 싶을 때 이중부정을 이용한다. - `!!'hello'` true - `!!NaN` false

# 2018-10-01 자바스크립트 3 일차

## null 과 undefined

- 변수를 선언한 적이 있는지 확인하고 싶을 때에도 typeof 연산자를 사용하고, 이 때 변수를 선언한 적이 없다면 'undefined'가 반환된다.

- 없음을 저장하기위해

```js
let foo; // 값을 대입한 적 없음
let bar = undefined; // 값을 대입함
foo; // undefined
bar; // undefined (??)


let obj1 = {}; // 속성을 지정하지 않음
let obj2 = {prop: undefined}; // 속성을 지정함
obj1.prop; // undefined
obj2.prop; // undefined (??)

둘다 없음이라는 사실을 나타내기는 하지만 개발자 입장에서 명시적ㅇ
```

- 자바스크립트에서는 없음을 나타내는 값이 두가지가 있다.
  - null
  - undefined

### null check

- 값이 있는지 ( 어떤 값이 null 도 아니고 undefined 도 아닌지)
- 값이 없는지 ( 어떤 값이 null 이거나 undefined 인지)

- 두개짜리 등호를 사용하면 null == undefined 가 된다

```js
null == undefined; // true
null === undefined; // false

//null은 undefined 외에는 모두 false
null == 1; // false
null == ""; // null
```

## 함수

- return 구문이 실행되면 `함수`가 즉시 종료된다.

### 스코프

- 변수의 유효범위 : 스코프
- 매개변수의 유효범위 : 함수 스코프

* 함수가 중첩되어있다하더라도 바깥쪽 매개변수는 안쪽에서 사용할 수 있다.
* 스코프는 위쪽으로만 따라갈 수 있다.

- 코드가 아주 길어졌을때 바깥쪽 변수와는 상관없이..

### 값으로서의 함수

- 값: 변수, 배열에도 저장할수있고 인수로도 넘길수있고.. 함수도 값이다
- {속성이름 : 속성값}
- 1 급 객체(@면접)

### 화살표 함수

- 매우 간단.
- return 을 써주않아도 return 가능
- 익명함수밖에 없다.
- function keword 함수처럼 사용하고 싶을때는 {중괄호}로 둘러싸서 사용할 수 있다.
- 표기법이 간단하기 때문에 다른 함수의 인수로 넘길 때 주로 사용.

### function 키워드 함수

- 값을 반화하려면 return 이 필수

## 제어구문

### switch

- break 가 없으면 다음 case 를 확인후 진행이 아니고 다음 케이스의 결과가 실행된다.

```js
switch (english) {
  case "red":
    result = "빨강색";
  // break;
  case "blue":
    result = "파랑색"; //브레이크가 없으면 여기로 넘어감
    break;
}
```

### 반복문

- do...while
  - do 안의 구문이 무조건 한번 실행된다.

### continue, break

- 가장 가까운 루프에 효과를 준다.

### 함수를 즉시 종료하기

1. return

- return 이 실행되는 순간 함수 바깥으로 빠져나옴.
- break 가 꼭 필요한 switch 문 같은 경우 return 이 있으면 break 를 생략해도 된다.
- 반복문만이 아닌 함수 자체를 종료시킴.

1. throw

- return 보다 더 큰.
- 지금 실행되고있는 많은 함수들을 종료시킨다.

# 2018-10-02 자바스크립트 4 일차

## 객체

- 자료구조(무언가를 담을 수 있는, 객체, 배열)
- 중괄호를 사용해서 객체를 사용할때 쓰는 : 객체 리터럴
- 식별자 규칙을 만족하는 속성 이름을 사용할 떄는 따옴표를 생략해도 된다.
- 객체 리터럴에서 속성값을 입력할 때 표현식을 입력할 수 있다.
- 내가 사용하고 있는 변수로 속성 이름을 만들고 싶을 때
  - 2 번, 3 번 예제 확인

```js
const name = "윤아준";

const person = {
  // 왼쪽 : 속성 이름이 될 문자열
  // 오른쪽 : 속성 값이 될 표현식
  name: name,
  age: 19
  // ...
};
```

```js
//총정리

const propName = 'prop3';

const obj = {
// 아래 두 예제는 왼쪽 부분이 문자열로 간주된다.
// 그리고 그 문자열이 그대로 속성 이름으로 사용된다.
  prop1 : 1, // prop1이 속성 이름이 된다.
  'prop2' : 2 // prop2가 속성 이름이 된다.

  //아래 예제는 대괄호 내부의 표현식의 결과값이 속성 이름으로 사용 된다.
  [propName]: 1 // prop3이 속성 이름이 된다.
  [propName + propName] : 1 // prop3prop3이 속성 이름이 된다.
};

// 아래의 표기법들은 주로 '코드 작성 시점에 속성 이름을 알 수 없는 경우'에 사용된다.
```

### 점 표기법

- 속성을 객체 리터럴을 이용해서만 만들 수 있는건 아니다.
- 객체가 만들어진 뒤에 추가 가능
- person.name ( .name : 속성접근자)
- 식별자규칙을 만족하는 경우에만 사용할 수 있음.

### 대괄호 표기법

- 식별자규칙에 맞지 않는 경우에는 대괄호 표기법 사용)
- 대괄호 안에 들어가는건 표현식이다.

### 객체 다루기

- `'name' in person; // true` : person 이라는객체 안에 name 이라는 속상이 존재하는지 확인

### 메소드

- 객체에 함수를 담아서 쓰는 경우가 아주 많다,

### this

### 생성자(constructor)

- 어떤 함수 앞에 new 를 만들면 객체가 만들어진다.
- new 로 함수를 호출하면 객체가 만들어짐 this 는 이 객체를 가리킨다.
- 어떤 함수가 생성자로 사용 될 예정인지 아닌지를 알려주는 관례로 첫글자를 대문자로 사용한다.(Person)

### 인스턴스(instance)

- 객체를 만들어내는 틀로부터 금방 생성 된 어떤 것

## 배열

- [배열로부터 새로운 값 생성] 밑에 있는 배열들은 원본 배열들을 자르지 않는다. 그 위에 있는 것들은 전부 원본 배열을 수정함.

### 배열 순회하기

#### for 구문

#### for..of 구문

- 변수를 계속 새로 만들어서 let 대신 const 를 사용할수있다.(근데안씀)
- 블록 스코프를 가진다. (해당 구문에서만 돈다)

### 배열로부터 새로운 값 생성

#### slice

- 인수값을 입력하지 않으면 (0, arr.length)가 된다.
  - => 원본배열과 똑같은 배열이 복사됨.
  - 원본 배열은 그대로 두고 그 배열의 복사본만을 수정하고 싶을때 사용

#### map ★★★★★

- 함수를 적용해서 그 반환값을 갖는 새로운 배열을 만든다.
- forEach 와 같이 세 가지 인수를 넘긴다.(item, index, array)

#### every

- every 는 predicate(판별함수)을 인수로 받아서, 모든 요소가 조건을 만족하는 지를 검사합니다.

# 2018-10-04 자바스크립트 5 일차

## 객체 추가 내용 (13 번 예제, 33 번예제 ★)

### 프로토타입 (★)

- 객체를 만들때마다 함수를 새로 만들어서 돌리는거는 메모리를 낭비하는 일이다.
- 비슷한 객체들이 공유하는 속성을 한 곳에 모아두자. => 프로토타입
-
- `Object.setPrototypeOf(child, newParent);` = child 의 프로토타입을 newParent 로 바꾼다.

```js
const parent = {
  familyName: "윤"
};
const child = Object.create(parent);

Object.getPrototypeOf(child) === parent; // true

console.log(child.familyName);

const newParent = {
  familyName: "신"
};
Object.setPrototypeOf(child, newParent);
Object.getPrototypeOf(child) === parent; // false

console.log(child.familyName);
```

- 객체 리터럴을 쓸때는 자동으로 프로토타입이 지정된다. = Object.prototype (이거는 규칙)

- 객체의 부모가 있고 부모의 속성을 사용 할 수 있다.

- 계속 이어져있는 프로토타입을 프로토타입

### 프로토타입을 간접적으로 변경하는것은 불가능

- 자식객체의 프로토타입을 통해서 객체를 삭제하는것은 불가능하다.

- 가장 가까운 객체

- instance 의 부모님 생성자는 .prototype
- new 로

### this: (function keword 함수로 만들어진 메소드 내부의 this 는) 호출되는 시점에 결정된다.

- 정의하는 순간 결정되지 않음..

### constructor

- 객체에 .constructor 속성에는 생성자가 들어있다.

## 배열 추가 내용

### reduce

- 많이 쓰임
- reduce 에 인수로 넘기는 함수에는 초기 누적값 0 이 있다.
- 함수의 반환값이 누적값이
- 초기값 0 을 주지않으면 첫번째 요소가 초기값으로 지정된다.
  - 이상하게 계산되는 경우가 있어서 초기값을 항상 적어주는게 좋음.
- `★★★★★★★배열을 순회할때 순회중인 배열을 편집해서는 안된다!! ★★★★★★★`

# 2018-10-10 자바스크립트 n 일차

## 값 더 알아보기

- 교재의 예제들을 돌려볼 때 let, const 를 var 로 바꿔서 돌려보자.

- `let`, `const`

  - 같은 이름을 갖는 변수의 재선언을 허용하지 않는다.
  - 변수가 선언되기 전에 참조하려고 하면 에러가 난다.
  - 블록 스코프를 갖는다.

- `var`

  - if 문 안에 있을지라도 함수 스코프를 갖는다. (함수의 매개변수나, var 변수는 함수 스코프를 갖는다.)
  - 선언되기 전에 가져와서 쓸 수 있다.
  - 호이스팅

- `if`, `for`, `while`, `function` 등의 구문을 사용하면 블록이 형성되어, 그 안에서 `let`, `const`를 통해 선언된 변수는 외부에서 접근 할 수 없다.

- 특별한 기능이 없는 블록을 만들 수도 있다.

```javascript
{
  let i = 0;
  console.log(i);
}
{
  let i = 0;
  console.log(i, "a");
}
{
  let i = 0;
  console.log(i, "b");
}
{
  let i = 0;
  console.log(i, "c");
}
```

- 호이스팅 hoisting

```javascript
function print() {
  console.log(foo);
  var foo = 5;
}

//호이스팅 되면 자바스크립트 리더기는 var foo; 를 끌어올려 읽는다
function print() {
  var foo;
  console.log(foo);
  foo = 5;
}
```

### 전역 변수 Global Variable

- ★★★★★★ 변수를 명시적으로 (예제 13 번)

### 전역 객체 Global Object

- 교재에 오류가있당. `let foo`가 아니고 `var foo`로 해야 `window.foo`가 확인이 된다.
- let 변수는 전역 객체의 속성이 되지 않는다.

### 참조 Reference

- typeof 랑은 다른 타입.
- object 를 제외한 6 가지 타입은 원시타입이다.
- Boolean / null / undefined / number / string / symbol / object

### 함수 호출

- 2.6 함수 챕터의 4 번 예제를 같이 확인
- obj 라는 객체를 인수로 넘길 때에는 원본이 변경된다
- 원시타입( 객체 배열 함수가 아닌 타입들)을 인수로 넘길때는 원본이 변경 될 수 없지만 참조타입이 인수로 넘어갈 때는 원본이 변경 될 수 있다.(2.6 함수 챕터의 4 번 예제와 함수호출의 17 번 예제를 비교해보자)
  - obj 라는 변수는 heap 내부의 객체{}를 참조한다.
  - 17 번 함수가 작동할 때 obj 의 참조(화살표)가 함수에 들어간다.
  - o 와 obj 는 같은 객체{}를 각각의 화살표로 동시 참조한다.
  - o 가 객체의 내용을 바꾼 순간 obj 도 같이 참조하고있기 때문에 같이바뀐다..

### 객체의 같음 Equality

- 등호 연산자는 같은 객체를 가리키고 있는지 확인

### 불변성 Immutability

- 원시타입은 원본을 변경할 방법이 없다.
- 자바스트립트의 원시타입의 값은 불변.
- 원시타입의 원본 값을 바꾸려면 재대입을 해줘야한다.
- 객체는 가변이지만 ( 프로그래밍 중에 원본 값이 변했을까봐 하는 걱정 때문에 ) 불변으로 만들어 프로그래밍 하기도 한다. => `Object.freeze(input)`
  - 중첩 된 객체는 얼리지못한다.

## 함수 더 알아보기

### 객체로서의 함수

### 주인없는 this

- 생성자도 아니고 메소드도 아닌 곳에서 this 를 출력하면 전역객체인 window 가 출력된다.

#### bind

```js
function printGrade(grade) {
  console.log(`${this.name} 님의 점수는 ${grade}점입니다.`);
}

const student = { name: "Mary" };
const printGradeForMary = printGrade.bind(student);
// .bind를 이용해서 this를 바꿔치기 하는 새로운 함수를 만듦.
// .bind : this가 고정된 새로운 함수를 만드는 것.

printGradeForMary(100); // Mary 님의 점수는 100점입니다.
```

#### call, apply

```js
function printGrade(grade) {
  console.log(`${this.name} 님의 점수는 ${grade}점입니다.`);
}

const student = { name: "Mary" };

printGrade.call(student, 100); // Mary 님의 점수는 100점입니다.
// 해당 함수를 실행하는데 this는 student로 하고 첫번째 인수를 100으로 하라
printGrade.apply(student, [100]); // Mary 님의 점수는 100점입니다.
// 해당 함수를 실행하는데 this는 student로 하고 첫번째 인수를 100으로 하라.
// 인수를 넘겨주는 방식이 다르다.

// 임시로 this를 바꿔치기 한 채로 함수를 실행시킬 수 있다.
```

### arguments 와 나머지 매개변수(Rest Parameters)

- arguments 는 여러가지 제약상황이 있기 때문에 요즈음에는 사용하지 않는것이 관례가 되었다.
- 대신 아래를 사용

```js
function sum(...ns) {
  // let result = 0;
  // for (let item of ns) {
  //   result += item;
  // }
  // return result;
  return ns.reduce((acc, item) => acc + item, 0);
  // ...ns를 하면 1 ,2, 3, 4를 다 담고 있는 `배열`이 ns에 저장된다.
  // ns가 배열이기 때문에 배열의 메소드인 reduce를 사용할 수 있다.
}

sum(1, 2, 3, 4); // 10
```

### 화살표 함수 Arrow Function

- function 으로 정의된 함수는 모두 prototype 을 가지고 있다.
- 화살표 함수의 this 는 정의된 문맥에 따라 결정된다( function 함수의 this 는 호출 될 때 결정된다.)
- [화살표 함수의 this](https://repl.it/@bbgrams/arrow-function-this)

### 매개변수의 기본값 Default Parameter

```js
// 'Mary'가 `name` 매개변수의 기본값이 됩니다.
function hello(name = "Mary") {
  // 코드가 훨신 더 깔끔해졌습니다!
  console.log(`Hello, ${name}!`);
}

hello("John"); // Hello, John!
hello(); // Hello, Mary!
hello(undefined); // Hello, Mary!
```

# 2018-10-11 자바스크립트 n 일차

## 함수형 프로그래밍

### 고차함수 (Higher-order Function)

- 함수를 인수로 받거나 함수를 반환하는(`bind`) 함수
- `ForEach`, `map`, `reduce`, `filter`, `sort`, `every`, `some`, `find`, `bind` 등
- 다른 함수의 인수로 넘겨지는 함수를 `콜백(callback)`이라고 한다.

### 클로저 (Closure) ★★

1. 바깥 스코프에 있는 변수를 가져다가 사용하는 함수
1. 변수가 저장되는 저장공간

### 화살표 함수와 고차 함수

- 10 번 예제는 7 번예제와 같다.
- 10 번 예제 : 화살표 함수를 반환하는 화살표 함수

### 재귀 함수 Recursive Function

- 자기 자신을 호출하는 함수

#### 루프와 재귀함수

- 문제를 같은 형태의 부분문제로 쪼갤 수 있을 때, 재귀함수를 활용할 수 있다.
- 실행 흐름이 일시중지했다가 재게하는것을 계속 반복한다.
- 재귀함수를 작성할 때는 :
  1. 부분 문제
  1. 종료 조건 (`sumBy(1) = 1`)
- [예제 sumBy](https://repl.it/@bbgrams/Recursive-Function-sumBy)
- [예제 fibo](https://repl.it/@bbgrams/Recursive-Function-fibo)

#### 분할 정복 (Divide and Conquer)

---

## 객체 더 알아보기

### 객체 자신의 속성 (Own Property) ★

- 속성접근자( 대괄호표기법, 점표기법..)을 ..

### 데이터 속성의 부수속성

- `Object.getOwnPropertyDescriptor` 라는 정적 메소드를 사용해 ~ **descriptor**라고 한다
- 데이터 속성에 대한 descriptor 는 네가지 속성을 갖는다.
  1. `value`
  1. `writable`
  1. `enumerable`
  1. `configurable` : false 면 삭제가 안된다.
- `Object.getOwnPropertyDescriptors` 많은 속성의 descriptor 를 한번에 보여준다.

### Descriptor(속성 기술자)를 통해 객체의 속성 정의하기

- `Object.defineProperty` 혹은 `Object.defineProperties` 정적 메소드를 사용해서 이미 만들어진 객체에 대한 속성을 정의할 수도 있다
- 이 때, enumerable 을 설정해주지 않으면 기본값으로 false 처리된다.
- Object.getOwnPropertyDescriptor()

### 접근자 속성(Accessor Property)과 그 부수속성

- `getter` 저장된 값을 가져올 떄는 getter 함수가 실행된다. -속성에 접근만 해도 getter 가
- `setter` 속성의 값을 정의했을때는 setter 함수가 실행된다.

### 객체의 속성 열거하기

- `keys` : 객체 자신의 속성만 반환한다.
- `values`
- `entries`
- [예제 16](https://repl.it/@bbgrams/object-property-enumerable)

### 얕은 복사(Shallow Copy) & 깊은 복사 (Deep Copy)

- `Object.assign` ( 얕은 복사 )
  - 객체를 병합한다.
  - 객체를 복사할때도 사용한다.
  - 객체가 중첩되어 있을때는 내부에 있는 객체는 복제되지 않고, 내부의 참조가 복사된다. ( 배열의 slice 도 마찬가지 )
  - [예제 19](https://repl.it/@bbgrams/shallowCopy-object-assign)

### Object.preventExtensions

- 객체에 속성을 추가하는 것을 막는다.

# 2018-10-12 자바스크립트 n 일차

## 연산자 더 알아보기

### 표현식

### 단축 평가 Short-circuit Evaluation ★★★

- AND :
- OR : 왼쪽이 truthy 이면 왼쪽 반환, 오른쪽이 truthy 이면 오른쪽 반환.왼쪽이 falsy 이면 오른쪽은 실행해보지도 않고 왼쪽을 반환하다.,,/??

### 삼항 연산자 Ternary Operator

-

### 증가/감소 연산자 Increment/Decrement Opertator

- 졸.려.
- // this.\_count++와 ++this.\_count 의 차이점을 확인해보자.
- https://repl.it/@bbgrams/SqueakyBothBoard

### 할당 연산자 Assignment Operator

- `--j` = `j-=1`
- `=` 는 오른쪽부터 실행된다. `let a,b,c,d; a = b = c = d = 1

### 연산자 우선 순위 Operator Precedence

### 연산자 결합 순서 Operator Associativity

- 결합 순서와 계산 순서가 같지 않을 수 있다.
- 삼항연산자는 오른쪽부터 결합이 되지만 계산은 왼쪽부터 된다.

### 값을 비교하는 여러가지 방법

#### 추상적 동일성

#### NaN 을 비교하려면 == 등호로는 안되고 Number.isNaN 으로만 비교 가능.

#### 엄격한 동일성 Strict Equality

#### Object.is

### 펼침 연산자 Spread Syntax (..새로운 연산자들) - edge 에서는 사용이안됨.

- 얕은 복사만 된다.
- 배열, 객체 안에 ...a 를 여러 번 넣을 수 있다.

#### 배열

#### 객체

- 객체 안에 같은 속성을 두번 정의하면 나중에 정의 된 속성만 적용된다.

### 분해대입 Destructuring Assignment ★★★★

#### 배열의 분해대입

#### 객체의 분해대입

- 속성 이름이랑 변수 이름이 같다면 생략이 가능하다.
- 34 번 예제보다 35 번 예제 방식을 아주 많이 사용.
- 화살표 함수에서 객체를 바로 반환하고 싶은 경우 괄호로 객체를 둘러싸주어야 한다.
- 39 번 예제 : arr 이라는 변수가 만들어지는것이 아니고 값이 선언되는 a,b,c 가 만들어지는것.

# 2018-10-15

## 내장 객체 및 생성자

### JSON 제이선 제이손 (Javascript Object Notation )

메모리에 저장된 배열, 데이터를 그대로 올릴 수 없으니까 텍스트 형식으로 변환한다. 이것을 직렬화라고 하고, 반대로 다시 변환하는 것을 역직렬화라고 한다.

- 예제 2 번 : 객체로 저장되어있는 정보들을 텍스트로 변환해 저장한다.
- `JSON.stringify(a)` : 직렬화
- `JSON.parse(a)` : 역직렬화
- JSON 을 직접 편집해야 할 때는 JSON 이 Javascript 가 아니라는 점을 주의
  1. 속성 이름은 꼭 쌍따옴표를 둘러주어야 한다.
  1. 복잡한 동작방식의 객체를 사용할 수 없다.
  1. 함수는 변환할 수 없다.
  1. 저장할 수 있는 정보가 한정되어있다.(함수불가)
  1. 객체 데이터를 직렬화-역직렬화 할때는 항상 신경써야한다.

### Date

Javascript 에 내장되어있는 생성자.

- 협정세계시 ★★★★★
- 유닉스시 ★★★★★

- 시간이라는 특별한 객체
- JSON 이 시간이라는 데이트 객체를 저장할 수 없기때문에 유닉스 Date 에서 추출한 시간을 유닉스 시간으로 변경하여 제이슨으로 넘긴다.

#### 문자열로 변환

- `toLocaleString()` : 사용자의 위치에 따른 지역 언어로 시간을 출력 (서울, 한국어 / 캐나다, 영어)
- `toISOString()` : 국제표준 표기법으로 나타낸 시간. ( Z 가 붙어있으면 UTC 기준. )

#### 시간 간격 측정

```js
const start = new Date();

setInterval(() => {
  const end = new Date();
  console.log(`경과시간 : ${end - start} 밀리초`);
}, 1000);
// 1000밀리초 (1초) 마다 실행하라
// 콘솔창에 1초마다 지속적으로 내용이 출력된다.
```

#### 라이브러리 사용

`Date` 객체는 실무에서 사용하기엔 좀 부족한 부분이 많다. `moment.js`라는 라이브러리가 가장 많이 쓰인다.

### Symbol

- 새로운 원시타입(원시타입의 종류들 ★★★★★)
- 객체의 기능을 확장한다.(ex. 원래 객체는 for...of 구문을 사용할 수 없는데, 이걸 사용할 수 있도록 기능을 확장해준다.)
- `obj.mySymbol` mySymbol 이라는 문자열을 속성키로 갖는 속성을 갖고온다. = obj['mySymbol']
- 예제 8 `obj[mySymbol]`
- 심볼을 사용할 때는 항상 [대괄호]를 쓴다
- [내장 심볼 - iterator](https://repl.it/@bbgrams/Symbol-iterator)

### Map

- `Map` 객체 내부에 저장되는 키 값으로 객체를 쓸 수 있다.

### Set

- 집합 형태의 자료구조
- 중복된 데이터가 저장되지 않는다.
- 배열과 유사한 형태의 자료구조가 필요하지만 순서가 중요하지 않은 경우,

```js
//  set을 이용해서 배열 내부의 중복 된 요소 제거하기

function removeDuplicates(arr) {
  const set = new Set(arr);

  // Set을 배열 형태로 변경해서 반환하라.
}
```

> ctrl + D : 커서를 여러개 만들기, 두번 누르면 같은 단어들이 선택됨

### 추가내용

##### 객체의 속성키로 문자열과 심볼이 사용될 수 있다.

##### 개행 문자

- 맥 : LF ( `\n` )
- 윈도우 : CRLF ( `\r\n` )
- autocrlf

##### git

- merge conflict
