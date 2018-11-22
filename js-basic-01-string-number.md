---
title: 자바스크립트 기본 정리 01 - string, number
date: 2018-10-21 15:29:11
tags:
---

1. 괄호 안의 숫자가 정수인지 실수인지 판별.
    `Number.isInteger(n)` // true

1. `NaN` : 자기 자신과 같지 않은 값.

- `NaN`을 판별할 때

    - `Number.isNaM`
    - `Object.is`

    ```javascript
    const thisIsNan = NaN;

    // NaN은 부등호로 확인 불가능
    thisIsNaN === NaN; //false

    // 이렇게 확인
    Number.isNaN(thisIsNaN); // true
    Object.is(thisIsNaN, NaN); // true
    ```

1. 문자열을 number 타입으로 바꾸는 법

- `parseInt`, `parseFloat`

```javascript
parseInt("123"); // 123
parseInt("0x4d"); // 77 : 10진수로 변환
parseFloat("12.345"); // 12.345
```

1. 특정 문자열이 포함되어 있는지 확인하는 법(배열)

- `.includes`, `startsWith`, `endsWith`, `indexOf`

```javascript
"hello".includes("hel"); // true
"hello".startsWith("he"); // true
"hello".endsWith("lo"); // true
"hello".indexOf("lo"); // 3
```

1. 문자열의 특정 부분을 바꾼 새 문자열 생성 (배열)

```javascript
"hello bbgram".replace("hello", "welcome"); // 'welcome bbgram'
```

1. 문자열의 일부를 잘라낸 새 문자열 생성 (배열)

```javascript
"bbgram".slice(2, 5); // 'gra'
```

- _(0)_ b _(1)_ b _(2)_ g _(3)_ r _(4)_ a _(5)_ m _(6)_
- 이런식으로 글자 앞 뒤에 숫자를 매기고 해당 숫자만큼의 문자열을 잘라낸다.

1. 좌우 공백문자를 제거한 새 문자열 생성

```javascript
"  bbgram  ".trim(); // 'bbgram'
"  bbgram  ".trimLeft(); // 'bbgram  '
"  bbgram  ".trimRight(); // '  bbgram'
```

1. 좌우 공백문자를 추가한 새 문자열 생성

```javascript
// 글자 길이가 괄호 안의 숫자 만큼 늘어나고 모자란 부분은 좌/우측에 공백이 생성된다.
"bbgram".padStart(8); // '  bbgram'
"bb".padStart(3); // ' bb'

"bbgram".padEnd(8); // 'bbgram  '
```

1. 문자열을 특정 문자를 기준으로 잘라 새 배열 생성

```javascript
"as!long!as!you!love!me".split("!"); // ['as', 'long', 'as', 'you', 'love', 'me']
"aslong".split(""); //['a', 's', 'l', 'o', 'n', 'g']
```

1. 모든 문자를 소문자, 혹은 대문자로 변환한 새 문자열 생성

```javascript
"As Long".toUpperCase(); // 'AS LONG'
"As Long".toLowerCase(); // 'as long'
```
