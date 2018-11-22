# 2018-10-12 

# 브라우저 측 자바스크립트

[브라우저 측 자바스크립트](https://github.com/fds11/fds-dom-api)

## 실습

### Form Scripting 실습
[예제](https://codepen.io/dbeat999/pen/bMBpdE)

- `document.querySelector(selector)`
    - selector 부분에는 css 선택자 입력

```js
// console 창

document.querySelector('.typed-name')

const nameEl = document.querySelector('.typed-name')

nameEl.textContent = '뾰뵹'
```

- `document.querySelectorAll` 
    - 이 셀렉터랑 일치하는 모든 요소 객체를 찾아서  갖다준다.

```js
// console 창
document.querySelectorAll('div') // 현재 문서의 div들을 가져온다

const divList = document.querySelectorAll('div')// 가져온 div들을 변수 선언해줌

divList[0].textContent = '하항' // divlist의 0번째 div에 하항이라는 문구 삽입

```

- `el.querySelector(selector)`
    - el에는 가져온 거시기 그거를 넣는다..ㅠ
- 사용자로부터 입력받은 텍스트는 el.textContent로 합시다!
- 사용자로부터 입력받은 텍스트를 el.innerHTML에 대입해서는 **절대로** 안된다.
    - 사용자가 올린 이상한 스크립트(바이러스, 해킹 등)가 innerHTML에 들어가면 그 스크립트가 다른 사용자들에게서 실행 될 수 있으므로 위험하다.
    - Cross-site Scripting (XSS)


- classㄹ ㅏ는 attribute, .genter라는 attribute value
- name 이라는 attribute, gender 라는 attribute
- reqired 는 boolean attribute


- class 를 추가할 때는 setAttribute를 사용하지 않고 classList.~를 사용한다.

- 인라인 스타일  조작 `el.style`

- 랜덤 색상코드를 만들어서
랜덤 눌렀을때 폼 색깔이 랜덤으로 변하게

### DOM 엘리먼트 생성하기

- `document.createElement('div')`
    - 메모리 상에 div를 하나 만들은 상태지만 아직 html 문서 안에 들어가있진않다.
    - DOM 객체는 문서 안에 있을수도 있고 바깥에 있을수도 있다.

### DOM 트리 조작하기

- `el.appendChild(newChild)` : 요소 끝에 자식 요소 삽입

```js
const formEl = document.querySelector('form')
const divEl = document.createElement('div')
divEl.textContent = '실습'
formEl.appendChild(divEl)
```

- `el.insertBefore(newChild, beforeWhat)` : 원하는 위치에 자식 요소 삽입

```js
const divEl2 = document.createElement('div')
divEl2.textContent = '두번쨰 div'
divEl2.style.color = 'pink' // 스타일 변경
divEl2.classList.add('div-el-2') // 클래스 추가
formEl.insertBefore(divEl2,divEl) // 요소 삽입
```

- 이미 문서 안에 존재하는 요소객체를 인수에 넣어서 호출하면 그 요소개체를 복사하지 않고 위치를 이동시킨다.
- 그래서 두 메소드는 위치를 이동시킬때도 사용한다.

- `el.replaceChild(newChild, oldChild)`
- `el.removeChild(child)`

```js
const linkEl = document.createElement('a')
linkEl.textContent = '구글링크'
linkEl.setAttribute('href', 'http://google.com')
fieldsetEl.replaceChild(linkEl, divEl2)
fieldsetEl.removeChild(linkEl)
```

### dataset

```html
<form action="https://httpbin.org/get" autocomplete="off" data-foo-bar = "hello" data-index="1">
```

```js
const formEl = document.querySelector('form')
formEl.dataset.fooBar // "hello"
formEl.dataset.index // "1"
```

### 노드 간 관계

### 요소의 크기 및 위치

### 이벤트 객체

- `e.stopPropagation()`
- `e.target`
- `e.currentTarget`
이벤트를 실제로 일으킨 요소와 이벤트 리스너가 들어있는 곳은 다를 수 있다.

타겟은 이벤트가 실제로 발생한 요소
커렌트 타겟은 이벤트 리스너가 등록되어있는 요소

이 ㅇ벤트 리스너가 어디에 등록되어잇는지와는 상관없이 정말로 이벤트 일으키는곳을 가르킨다.

일부 이벤트들은 특정 타입의 요소를 위해 존재하는 이벤트이기때문에 캡쳐링만  일어나고 버블링은 일어나지않는다.

### 폼 이벤트
 
 - 자주 쓰이는 몇가지만 사용해보자.
 - `change` 
 - [폼 이벤트](https://codepen.io/Shim-SoYoung/pen/YJEbVa)
 - [폼 -브라우저 내장 기능](https://codepen.io/Shim-SoYoung/pen/jeaoKP)
 - 요즘은 폼의 전송 기능을 잘 사용하지않는다. 하지만 그럼에도 불구하고 폼태그를 많이 사용한다. 왜냐면 전송기능 말고도 여러가지 편리 기능이 내장되어있다. 예를들면 엔터 쳤을 때 자동으로 전송되는 동작.




### 마우스 이벤트

- [마우스 이벤트 실습, 드래그엔드롭](https://codepen.io/Shim-SoYoung/pen/Edbqdj)

 - Q. [mouseenter / mouseleave]와 [mouseover / mouseout] 의 차이점 ( e.target, e.currentTarget이 연결되어있다.)


### 키보드 이벤트
- 실습 : todolist




## 맽밑
전파단계를 거침
에드이벤트 리스너륽 ㅡ냥 사용하면 이벤트리스터가 다 버블링 단계에 들어온다. 마지막에 트루를 붙여주면 캡쳐링 단계에 들어와서 이벤트가 어느 시점에 동작해야하는지 변경해줄수있다.

### 실습 1. 할일추가 목록

- 추가버튼을 클릭스 prompt 창을 띄워서 내용 삽입.
- `querySelector`는 서버 비용이 많이 들기 때문에 한 번만 호출하여 변수에 저장하고 변수를 호출한다.(??)

1. 첫번째 목록에서 '위로'버튼을 누르면 가장 밑으로 내려간다. 왜일까 ? => DevDocs 확인
1. 마지막 목록에서 '아래로'버튼을 누르면 에러가 발생한다. 왜일까 ? => DevDocs 확인

### Q2. to-do-list 마지막 목록에서 위로 버튼을 눌렀을 때 왜 맨 첫번째로 가는지

- 첫번째 요소에서 previousElementSibling을 하면 null이 된다.
- insertBefore의 두번째 인수에 null이 들어가면 appendChild와 똑같은 동작을 한다.


### Q3. to-do-list 마지막 목록에서 아래로 버튼을 눌렀을 때 왜 오류가 나는지 ?

- 오류 해석 :  null의 nextElementSibling을 읽을 수 없다
- 마지막 li의 nextSbling은 null이기 때문에,  null의  nextSbling을 가져올 순 없기때문에 오류가 난다.




### 책 추천 : 자바스크립트 완벽 가이드 ( 코끼리 책), 프론트엔드 개발자를 위한 자바스크립트 프로그래밍 (노란색)


### rgb game

- 자바스크립트로 동작을 두가지가있따.
    1. DOM 객체를 추가하는법(createElement)
        - 코드 작성 시점에 내가 실제로 몇개를 생성해야할지 모르는 경우 (사용자가 할 일을 몇개 추가 할지 모를때)
    1. style을 다르게 먹여서 생겼다 사라졌다(display none)
        - 코드 작성 시점에 내가 정확히 무엇인가를 표시하고자 하는지를 알고있을 때


### game을 만들 때 사고방식

- 화면, 사용자 입력, 시간경과, 상태(state)
- 사용자가 입력해서 맞거나 틀리면 상태가 바뀐다 => 화면 그리기
- 