# 2018-11-13

# 자바스크립트 심화2 - 예외 처리

예외 처리 : 코드 실행 중에 예기치 못한 에러가 발생했을 때 코드의 실행 흐름을 복구할 수 있는 기능

## 동기식에서의 예외처리
```js
try {
  console.log('try');
  new Array(-1); // RangeError: Invalid array length
} catch (e) {
  console.log('catch');
} finally {
  console.log('finally');
}
```

## 직접 에러 발생시키기

## 비동기식 코드에서의 예외 처리

### 콜백

### Promise

```js
p.then(even => {
  return '짝수입니다.';
}, e => { // then 메소드의 두번쨰 인수로 실패했을때의 함수를 보낸다.
  return e.message;
}).then(alert);
``` 
```js
p.then(even => {
  return '짝수입니다.';
}).catch(e => { // then 메소드도 promise를 반환한다
  return e.message;
}).then(alert);
```
```js
Promise.resolve()
  .then(() => {
    throw new Error('catch 메소드를 통해 예외 처리를 할 수 있습니다.');
  })
  .then(() => {
    console.log('이 코드는 실행되지 않습니다.');
  })
  .catch(e => { // then..catch는 try..catch 느낌이다.
    return e.message; 
  })
  .then(console.log);
```

### 비동기 함수
비동기 함수인 경우 rejected 상태의 promise를 await하면 에러가 발생하고 그 에러는 try...catch 블록으로 잡아낼 수 있다
```js
async function func() {
  try {
    const res = await fetch('https://nonexistent-domain.nowhere'); // 없는 주소 
  } catch (e) {
    console.log(e.message);
  }
}

func(); // 출력 결과: Failed to fetch
```

단, rejected promise를 await하지 않으면 에러가 잡히지 않는다.

# 2018-11-14 모듈
# 모듈

1. 일반 자바스크립트와는 달리 특수한 

## 모듈 스코프 - 모르겟슴


## export & import

- 다른 모듈에 정의된 값을 가져오는 문법
- 다른 모듈에 있는 이름을 사용하려면 반드시 이름을 `export` 해주어야 한다.
- 모듈 스코프에서 정의된 이름은 export 구문을 통해 다른 파일에서 사용할 수 있습니다. 이를 '이름이 지정된 export'라는 뜻에서 named export라 부릅니다.

```js
// variables.js 파일에서
const foo = "bar";
const spam = "eggs";
export { foo, spam }; // 나는 이 이름들을 다른 파일에서 쓸 수 있도록 만들어주겠다.

```
```js
// index.js 파일에서
import{foo, spam} from './variables'
console.log(foo, spam)
```

## 선언과 동시에 export 하기

- 이름을 선언하는 구문 앞에 `export`를 붙여주면 선언과 동시에 export를 한번에 할 수 있다.
```js
export const foo = "bar";
export const spam = "eggs";

export function add(x, y) {
  return x + y;
}
```
- 값을 `export` 하는게 아니고 **이름**을 `export` 하는 것이다.

## default export
- 모듈을 대표하는 하나의 값을 지정하고 그 값을 다른 모듈로 불러온다
```js
// foo.js

export default 'bar'; // 대표하는 하나의 값
```
```js
// main.js

import foo from './foo.js' // import 부분에 쓰고싶은 이름을 쓸 수 있다. 이름을 넘겨준 것이 아니고 값을 넘겨준 것이기 때문에. {}중괄호도 쓰지않음

console.log(foo); // bar
``` 

- `import` 구문에서 default export와 일반적인 export를 동시에 가져올 수 있다.
```js
// `React`라는 이름의 default export와,
// Component, Fragment라는 일반적인 export를 동시에 가져오기
import React, { Component, Fragment } from 'react';
```
```js
export default class{

}
export const Component = "..";
export const Fragment = "..";
```


## 다른 이름으로 export & import 하기

```js
import {foo as FOO} from './variables'
console.log(FOO)
```
```js
export * from ...  // import 한 모듈들의 이름을 그대로 사용하여 바로 export 하겠다.

```
## 모듈 사용 시 주의할 점
- 같은 모듈을 여러 다른 모듈에서 불러와도, 모듈 내부의 코드는 단 한 번만 실행된다.