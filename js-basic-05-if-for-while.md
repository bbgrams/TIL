---
title: 자바스크립트 기본 정리 05 - 제어구문(조건문, 반복문)
date: 2018-10-23 19:57:55
tags:
---

## 조건문 (Conditional Statement)

### 1. `if...else` 구문

```javascript
function roll(){
  return Math.ceil(Math.random() * 6) // 1 ~ 7까지의 랜덤한 숫자
}

function game(){
  const result = roll(); // roll 함수 호출
  
  alert(`결과 : ${result}`);
  
  if ( result >= 4){
    // 괄호 안의 결과값이 true 이면
    alert ('승리');
  }else {
    // 위의 괄호 안의 결과값이 false 이면
    alert('패배');
  }
}

game() // game 함수 호출
```

1. `else`가 필요없는 경우에는 `else`를 생략할 수 있다.

1. 중괄호 내부에 들어있는 구문이 하나라면 중괄호를 생략할 수 있다

    ```javascript
    if(result === 7) alert('럭키!');
    ```

1. `if ..else`

    ```javascript
    function translateColor(english) {
      if (english === 'red') {
        return '빨강색';
      } else if (english === 'blue') {
        return '파랑색';
      } else if (english === 'purple' || english === 'violet') {
        return '보라색';
      } else {
        return '일치하는 색깔이 없습니다.';
      }
    }
    ```

### 2. switch 구문

```javascript
function translateColor(english){
  let result;
  switch(english){
    case 'red' :
      result = '빨강색';
      break;
    case 'blue' :
      result = '파랑색';
      break;
    case 'purple' :
     result = '보라색';
     break;
    default : 
      result = '일치하는 색상이 없습니다'
  }
}
```