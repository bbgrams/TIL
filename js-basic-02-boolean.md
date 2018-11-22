---
title: 자바스크립트 기본 정리 02 - boolean
date: 2018-10-22 15:29:11
tags:
---

1. 연산자 우선순위 (Operator Precedence)

- AND(&&) 연산 > OR(||) 연산

```javascript
true || true && false // true
(true || true) && false // false
true || false && false // true
(true || false) && false // false
```

1. 논리 연산의 여러가지 법칙

- a, b, b 가 **모두 bollean 타입** 이라고 할 때, 다음 식의 결과값은 a, b, c 의 값과 관계 없이 모두 true 이다.

```javascript
// 이중부정
!!a === a;

// 교환 법칙
a || b === b || a;
a && b === b && a

// 결합 법칙
(a || b) || c === a || (b || c)
(a && b) && c === a && (b && c)

// 분배 법칙
a || (b && c) === (a || b) && (a || c);
a && (b || c) === (a && b) || (a && c);

// 흡수 법칙
a && (a || b) === a;
a || (a && b) === a;

// 드 모르간의 법칙
!(a || b) === !a && !b;
!(a && b) === !a || !b;

// 그 외에
a || true === true;
a || false === a;
a && true === a;
a && false === false;

a || !a === true;
a && !a === false;
```

1. truthy & falsy

**falsy**

- `false`
- `null`
- `undefined`
- `0`
- `NaN`
- `''` (빈 문자열)

이를 제외한 모든 값들은 **truthy**

1. 다른 타입의 값을 진리값으로 변환하기

```javascript
!!"bbgrams"; // true
Boolean("bbgrams"); // true
```
