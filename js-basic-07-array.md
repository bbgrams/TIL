---
title: 자바스크립트 기본 정리 06 - 배열(Array)
date: 2018-11-13 18:06:55
tags:
---

# 배열

- 배열 안에 들어있는 값들을 **요소(element)** 혹은 **항목(item)** 이라고 한다.
- 배열에는 순서가 있다.
- 배열은 `Array` 생성자의 인스턴스이다. **배열의 프로토타입으로 `Array.prototype` 객체가 지정되어있다 **

## 배열 생성

```js
// 배열 리터럴
const arr = [1,2,3];

// Array 생성자 - 비추
new Array(1); // [empty]
new Array(10); // [empty * 10]

// Array.of
Array.of(1,2,3);
Array.of(1); // [1]

// Array.from
Array.from('bbgrams');//["b","b","g","r","a","m","s"]
```

## 요소 읽기

- 인덱스(index)를 이용해 읽을 수 있다.
- 0부터 시작

## 요소 수정하기
```js
const arr = [1,2,3,4,5]
arr[1] = 99; // [1,99,3]

// 전체를 0으로 채우기
arr.fill(0); // [0,0,0,0,0]

// 인덱스 2와 4 사이를 1로 채우기
arr.fill(1,2,4) // [0,0,1,1,0]

// 5로 채운 길이 100의 배열 만들기
new Array(100).fill(5)
```

## 배열에 요소 추가/제거

```js
const arr = [1,2,3];
```

### 끝 부분에 요소 추가- push

```js
arr.push('hi') // [1,2,3,'hi']
arr.push('bb') // [1, 2, 3, 'hi', 'bb']
```

### 끝 부분의 요소 삭제 - pop
- 배열에 요소가 없는데  pop()을 할 경우 `undefined`를 반환한다.

```js
arr.pop() // [1, 2, 3, 'hi']
arr.pop() // [1, 2, 3]
```

### 시작 부분에 요소 추가 - unshift

```js
arr.unshift('hi') // ['hi', 1, 2, 3]
arr.unshift(7, 10) // [7, 10, 'hi', 1, 2, 3]
```

### 시작 부분의 요소 삭제 - shift
- 배열에 요소가 없는데  shift()을 할 경우 `undefined`를 반환한다.

```js
arr.shift() //[10, 'hi', 1, 2, 3]
arr.shift() // ['hi', 1, 2, 3]
```

### 배열 중간에 삽입하기 - splice

```js

```