# 2018-11-12 리액트 1일차

[리액트 한글화](https://reactjs-org-ko.netlify.com/tutorial/tutorial.html)

```js
class ShoppingList extends React.Component { // 1.
  render() {
    return (
      <div className="shopping-list"> 
        <h1>Shopping List for {this.props.name}</h1>
        <ul>
          <li>Instagram</li>
          <li>WhatsApp</li>
          <li>Oculus</li>
        </ul>
      </div>
    );
  }
}

// 사용 예제: <ShoppingList name="Mark" />
```
```
위에서 본 ShoppingList는 React 컴포넌트 클래스입니다. 컴포넌트는 props (“properties”의 줄임말)이라 불리는 매개변수를 받아서, render 메소드에서 뷰의 계층 구조를 반환합니다.
```
1. Component는 클래스고 UI를 반환하는 render() 메소드를 가지고있다

1. 뷰 : 어떻게 그릴것인지 설명하는 값

1. shoppingList return 내부에 있는 코드들은 html이 아니다. 
    - 리액트 엘리먼트이다.
    - react div element, react h1 element..
    - 객체를 만들어내는 문법이다.
    - 값이다.
1. 중괄호 안의 {this.p~} 표현식은 textContent처럼 작동하게 할 수 있다.

1. 컴포넌트로 만들면 `<ShoppingList />`와 같이 쓸 수 있다.
    - 나중에 이 태그를 쓰면 shoppingList 내부의 div ul li값이 반환된다.

1. 중괄호 안에는 어떤 표현식이라도 다 들어갈 수 있다.
그리고 리액트는 그 표현식을 잘 그려준다.

1. 리액트 엘리먼트의 값이 들어갈 수도 있다.

1. 컴포넌트에서 컴포넌트로 데이터를 전송할 수 있다.

1. [리액트 - tic tac toe ](https://codepen.io/Shim-SoYoung/pen/PxGLNW)

1. 정보는 부모에서 자식으로 흐른다. 폭포수 처럼

1. 리액트에서 이벤트 리스너 등록하기  
    1. onClick 
    1. onSubmit
    1. onMouseover
    1. 이벤트 리스너를 줄때에는 꼭 괄호 안에 함수를 넣어주어야 한다.

```js
class Square extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: null,
    };
  }

  render() {
    return (
      <button className="square" onClick={() => this.setState({value: 'X'})}> 
        {this.state.value}
      </button>
    );
  }
}
```
1. setState★★★★★★★★

1. 클릭 시 `상태`가 바뀌게 코드를 작성해주었다.

1. setState를 이용해서 상태를 바꿔주면 React가 자동으로 화면을 다시 그려준다.

1. 우리는 화면을 다시 그려줄 필요가 없다. 상태를 바꿔주면 자동으로 화면을 다시 그려주니까.

1. 리액트에서는 화면을 다시 그리기 위해서는 상태를 바꿔주는 방법밖에 없다.(setState)

1. 리액트는 화면을 다시 그려야할 때마다 render()메소드를 계속 호출한다.

1. 리엑트에서는 자식 컴포넌트에 저장되어있는 상태를 부모 컴포넌트에서 불러오는 일은 없다.
    - 리액트에서는 그렇게 하지 않는다.
    - 이유는 이해하기 어렵고, 버그가 발생하기 쉽고, 수정하기 어려운 코드가 되기 쉽다.

1. 부모 컴포넌트에 상태를 두고 그 상태를 공유하는 방식으로 한다.

1. 상태를 공유해야하는 컴포넌트끼리의 가장 가까운 공동 조사에 넣는것이 좋다.

1. `여러 자식 컴포넌트에 저장되어 있는 데이터를 읽어와야 할 때, 혹은 자식 컴포넌트끼리 통신을 해야 할 필요가 있을 때는, 부모 컴포넌트에서 상태를 공유하세요. 부모 컴포넌트에서는 prop을 통해 자식 컴포넌트에게 상태를 내려줄 수 있습니다. 이 방법을 통해 부모 컴포넌트와 자식 컴포넌트가 따로 놀지 않게 만들 수 있습니다.`

1. 만약에 부모에서 상태를 바꾸는 함수를 만들어서 내려준다면 간접적으로 부모의 상태를 바꿀 수 있게 된다.

1. 내장 DOM 컴포넌트(button..)
1. 커스텀 컴포넌트(Square..)

1. 상태에 객체나 배열이 있을때는 항상 복사 후 넣어준다. - 불변성과 연관이있음

### 함수형 컴포넌트

1. 컴포넌트를 작성하는 방법에는  클래스 형태와 함수 형태가 있다.

1. 클래스 컴포넌트가 부모로부터 내려받은 값은 this.props에 저장되는데

1. 함수형 컴포넌트에서는 this에 저장할수없고

```js
function Square(props) {
  return (
    <button className="square" onClick={props.onClick}>
      {props.value}
    </button>
  );
}
```
1. props 매개변수에 객체가 들어오고 객체의 속성에 부모로부터 내려받은 값이 저장되었다.

1. render() 메소드만 따온거라고 이해해도 된다.


### 튜토리얼에서 중요한 내용들 훑어보기

1. React는 선언적이다.
1. 컴포넌트
1. 엘리먼트
1. 하나의 컴포넌트로 수많은 엘리먼트가 만들어질 수 있다.
1. React 엘리먼트는 무엇을 그릴지에 대한 내용을 담고 있는 `객체`이다. 
1. DOM객체가 아닌 React 객체이다.
1. props : 부모로부터 값을 내려받는 통로
1. 상태는 setState를 사용해서만 바꾼다.
1. 상태를 처음 만들어줄 때에는 생성자 안에서 만들어 주는 것이 원칙이다.
1. setState에는 상태 변경, 화면 갱신의 기능이 있다.
1. 상태를 공유해야
1. 상태를 바꾸는 함수를 z만들어서 자식한테 내려준다.
1. 자식에서 부모 상태를 바꾸고 싶은 경우, ` **상태를 바꾸는 함수를 만들어서 내려준다** `
1. UI를 값으로 다룬다 => map 등을 사용할 수 있다.
1. Board 컴포넌트 안에서 상태를 바꾸는 함수를 만들어서 Square에 내려준다.
1. React 16.6 버전은 더 많은 기능이 있다.
1. React 현재 개발하고 있는 버전에서는 Hook을 이용해서 함수형 컴포넌트에서도 생성자?를 만들 수 있다.



### [리액트 기초실습 1](https://codepen.io/Shim-SoYoung/pen/pQEXBG)
### [리액트 기초실습 2 - 짜장면](https://codepen.io/Shim-SoYoung/pen/bQwXwQ)
### [리액트 기초 실습 3 - 할일 목록](https://codepen.io/Shim-SoYoung/pen/mQObPo)

### 리액트로 실습하기 순서
1. 화면 그리기
1. 상태 설계(상태 기억)
1. 상태를 설정해주는 작업 (this.state = {count : 0})
1. setState

1. 리액트는 화면을 다시 그릴 때 마다 render를 많이 호출한다. 때문에 render 메소드 안에서는 화면을 그리는것과 관계있는 것만 적어야한다.!!

# 2018-11-13 리액트 2일차

# JSX 소개

- [https://reactjs-org-ko.netlify.com/docs/introducing-jsx.html](https://reactjs-org-ko.netlify.com/docs/introducing-jsx.html)

- JSX는 자바스크립트의 확장 문법이다.

### JSX에 표현식 포함하기

### JSX 어트리뷰트 정의
1. HTML 어트리뷰트를 넘길 때 `camelCase`를 사용해야 한다.
1. HTML 어트리뷰트의 이름 그대로를 사용하지 않는 경우도 있다.
  ```js
  const element = <img src = "{user.avatarURL}"></img>
  const element = <img className="profile-img"></img>

  <label htmlFor="my-input" ></html>
  <input id="my-input></input>
  ```

### JSX 자식 정의
1. 여는 태그만 있다면 XML처럼 `/>`를 이용해 닫아주어야한다.
```js
const element = <img src={user.avataUrl} />
```

### JSX 인젝션 공격 예방
1. XSS(cross-site-scripting)
    - 사용자가 입력한 내용에 스크립트가 들어있으면 XSS 공격을 당할 수 있다.
1. 리액트에는 보안기능이 내장되어있기 떄문에 방어가 된다.
1.  **innerHTML , textContent의 차이. XSS 위험도 확인**

### JSX 객체 표현


# 요소 렌더링
[https://reactjs-org-ko.netlify.com/docs/rendering-elements.html](https://reactjs-org-ko.netlify.com/docs/rendering-elements.html)

### DOM에서 요소 렌더링 하기
1. 리액트를 사용할때 우리는 두가지 라이브러리를 사용중이다
    - React DOM
    - React Native

### 렌더링된 요소 업데이트
1. 리액트 요소는 변경 불가능하다.
1. 불변성(immutability)
    1. 변경할 수 없다.
    1. ★★★값을 변경하고 싶을 때는 값을 새로 만든다★★★
1. 변경하고 싶다면 처음부터 새로 만든다.
1. 우리는 화면을 바꾸는 코드를 짜지 않았고 상태를 바꾸는 코드만을 짰지만 react는 상태가 바뀌면 render메소드가 다 호출되고 react element가 전부다 다시 생성된다.

### React는 꼭 필요한 부분만 갱신한다.
1. 우리가 그동안 만들었던 코드들은 (할일목록, 쇼핑몰) 비효울적으로 작동했다. ( DOM 트리의 모든것들을 다 지우고 싹 새로 만든다.)
1. React는 정말로 변경된 부분만 다시 그린다.
    - 이전에 그렸던 화면을 기억해뒀다가 다시 그릴 화면을 비교해보고 달라진 부분만 다시 그린다.
1. 우리의 경험상, ‘시간 경과에 따라 UI를 어떻게 변경할지’를 생각하는 것이 아니라 ‘특정 순간에 UI가 어떻게 보여져야 할지’에 대해 생각하면, 수많은 종류의 버그를 없앨 수 있습니다.

# 컴포넌트와 props
[https://reactjs-org-ko.netlify.com/docs/components-and-props.html](https://reactjs-org-ko.netlify.com/docs/components-and-props.html)

1. 컴포넌트롤 통해 UI를 독립적이고 재사용 가능한 부분으로 분리하고, 각 부분을 독립적으로 생각할 수 있다.

### 함수형 컴포넌트, 클래스형 컴포넌트

### 컴포넌트 렌더링

### 컴포넌트 조립하기
1. 최상위에 두는 컴포넌트는 `App`이라고 하는것이 관례이다.

### 컴포넌트 추출
1. 컴포넌트를 더 작은 컴포넌트로 쪼갠다

### props는 읽기 전용이다.
1. props는 수정하면 안된다. 
1. 입력을 변경하지않고 동일한 입력에 대해 항상 동일한 결과를 반환하는 함수를 `순수 함수`라고 한다
    ```js
    function sum(a, b) {
      return a + b;
    } 
    ```
1. 순수함수가 아닌것 :  Math.random()    
    ```js
    function withdraw(account, amount) {
      account.total -= amount; // account가 수정되므로 순수함수가 아니다
    }
    ```
1. 모든 React 컴포넌트는 props에 대해서는 순수 함수처럼 동작해야한다.
1. render 메소드 안에서는 Math.random같은 순수함수가 아닌 함수를 사용하면 안된다(?)

# State와 라이프사이클
[https://reactjs-org-ko.netlify.com/docs/state-and-lifecycle.html](https://reactjs-org-ko.netlify.com/docs/state-and-lifecycle.html)

1. 캡슐화 : 정보를 숨기는 행위

### 함수를 클래스로 변환

### Class에 로컬 state 추가하기
1. state를 넣을때에는 생성자를  만들어줘야한다.

### 클래스에 라이프사이클 메서드 추가하기
1. 화면에서 상태가 변경될때 화면이 그려져야하고
1. Clock이 DOM에 최초로 랜더링 되는 것 : mounting 마운팅
1. Clock 이 DOM에 최초로 렌더링 될 때 타이머를 설정 하려고 합니다. React에서 이를 “mounting” 이라고 부릅니다
1. 그리고 DOM에서 Clock 이 삭제되었을 때 타이머를 해제 하려고 합니다. React에서 이를 “unmounting” 이라고 부릅니다.
1. componentDidMount() : 컴포넌트가 마운트 되자마자
1. componentWillUnmount() : 컴포넌트가 언마운트 되기 직전
1. 특정 사이클 시점에 걸어넣는 다는 느낌으로 `라이프사이클 훅`이라고 한다.
1. 마운트는 컴포넌트가 돔에 장착되는 직후에 실행되고
언마운트는 컴포넌트가 돔에서 삭제 되기 직전에 실행된다.

### State 바르게 사용하기
1. state를 직접 수정하지말자
1. state 업데이트는 비동기일 수 있다
1. `this.props` 및 `this.state` 가 비동기로 업데이트될 수 있기 때문에, 다음 state를 계산할 때 이전 state 값을 신뢰해서는 안됩니다.
    - `{count: this.state.count + 1}`  이렇게 하지않기
    - 비동기적으로 .. 1씩 증가

1. 다음 상태를 이전 상태로부터 계산해내고싶을때는 setState에 함수를 써주어야한다.
    - `prevState =>{ return{count: prevState.count+1}}`
    - 콜백에 함수를 하나씩 넣고 하나씩 실행한다. : 2씩 증가


### State 업데이트는 병합된다.
1. state는 여러 독립적인 속성을 가질 수 있다.
1. 얕은 병합을 진행한다.
    - => 중첩되어있는 객체를 병합할때는 문제가 생길 수 있다.
    - 얕은 복사 : 객체 안의 객체, 또는 배열 안의 배열은 복사되지않음.
    - 얕은 병합 : 객체 안의 객체는 대체된다. 
1. state 안에 중첩된 객체를 사용하는것은 좋지않다.(객체 안의 객체, 배열 안의 배열)    

### 데이터는 아래로 흐른다.
1. state를자식한테 내려보낼 수 있다.

# 리액트 실습하기
## 실습하기- [rgb challenge](https://codesandbox.io/s/m7v8pvr3jy)
1. 화면 그리기
2. 상태설계 
3. 
4. 이벤트를 줬을 때 상태가 바뀌고 화면이 다시 그려진다.

- 버튼, 인풋같은 클릭기능이 있는곳에는 onClick만 적어도 자동이로 이벤트 리스너가 되는데 div가틍ㄴ 곳은 자동으로 이베느리스너가 달리지않기 때문에 직접 달아줘야한다.



# 이벤트 제어하기
[https://reactjs-org-ko.netlify.com/docs/handling-events.html](https://reactjs-org-ko.netlify.com/docs/handling-events.html)

1. 리액트에서는 비동기함수를 이벤트 리스너에 그냥 등록하는것은 위험하다.
1. 메소드를 그대로 이벤트 리스너에 등록하면 안된다. 
1. 그냥함수는 어떻게 호출되는지에 따라 this가 결정되기 떄문에 this를 찾을 수 없다.
1 .`this.handleClick = this.handleClick.bind(this);` 생성자 내부에서는 디스가 제대로 된 인스턴스를 가르키고 있을테고, 그 인스턴스로 고정시켜서 넘긴다.
1. 클래스의 메소드들은 프로토타입에 저장된다.
1. ... ㅇㅓ려워
1. bind 대신 화살표함수를 쓰자!
1. 이벤트 함수를 쓸때는 항상 화살표함수를 써주자! 그럼 this가 고정된다! 와~
    `<button onClick={() => this.handleClick()}>`

# 조건부 렌더링
[https://reactjs-org-ko.netlify.com/docs/conditional-rendering.html](https://reactjs-org-ko.netlify.com/docs/conditional-rendering.html)

1. 어떨때는 이 화면~ 어떨때는 저 화면을 보여주고 싶을 때 


### && 논리 연산자를 사용해 if를 인라인으로 넣기

1. 중괄호로 감싸면 어떤 표현식이든 넣을 수 있다.
```js
{unreadMessages.length > 0 && // 안읽은 메세지가 있으면 아래 태그를 그려라.
  <h2>
    You have {unreadMessages.length} unread messages.
  </h2>
}
```
1. react 는 false, null은 아무것도 그려주지 않는다.
1. 그래서 위에 && 연산자에서 앞에가 트루면 뒤에것을 반환한다.
&& 연선자는 앞에가 falsy이면 앞에꺼를 반혼하고 앞에가 트루면 뒤에걸 반환 
or 앞 트루 앞 반환 앞 펄시 뒤 반환

### 조건부 연산자를 사용해 if-else 인라인으로 넣기

### 조건부 렌더링을 할때는
1. 삼항연산자
2. || or 연산자
3. && and 연산자를 사용하자


# 2018-11-14 리액트 3일차

# 부록 - 리액트의 상태

- class의 instatnc가 실제로 생성되고 리액트 어딘가에 저장되어있어서 그 instance를 this라고 부른다.  그래서 this.state라고 하면 이 instance에 저장되어있는 값들이 불러진다.

- 화면에 표시가 되어야 그에대한 state를 가질 수 있다.
- 화면에 표시도 되지 않은 컴포넌트의 state가 살아있을 수 없다.
- 리액트의 **상태**를 이해하는게 아주 중요하다
- 함수형 컴포넌트는 instatnce를 붙일 수 없기 때문에 상태를 가질 수 없는것이다.
- 컴포넌트가 **그려져야** 상태를 가진다
- 게임 상태를 초기화 할 때 키를 바꿔주는 방법을 사용하기도 한다. ( 키를 바꾸면 그 전에 키에 저장되었던 상태가 다 날아가고 새로운 키에 새로운 상태가 그려진다.)


# 리스트와 키 

값으로서의 UI를 잘 다루는 방법

- map 메소드를 이용하여 <li>를 반복 출력할 때는 각자의 `key`를 항상 적어줘야 한다.

### 키
- 자료의 식별자를 키로 써주는 것이 가장 좋다.
- 배열 index를 키로 사용할 떄는 주의해야 한다.
    - 항목 간 순서가 바뀔 수 있는 경우 index를 사용하지 않는게 좋다.
    - 
- 리액트한테 배열을 그려달라고 요청할 때에는 키를 넣어줘야한다.
- 키를 쓸 때 주의할 점 
    1. 키로 쓸 때의 값(식별자)는 모두 다른 값이어야 한다.
- map에서 반환되는 element에 키를 넣어줘야한다.
- key는 아래에서 받아서 쓸 수 없다.
    ```js
    const content = posts.map((post) =>
      <Post
        key={post.id}
        id={post.id}
        title={post.title} />
    );
    ```
    - key와 ref는 컴포넌트 안쪽에서 받아서 쓸 수 없다.
    - `props.key`,  `props.ref` 는 **불 가 능**


# 폼

- 리액트에서 `form`을 다루는 방식이 아주 다르다
- HTML의 폼요소는 그 자체가 내부 상태를 가진다
    - input, select, textarea .. 등 폼 필드에 텍스트가 뭐가 입력됐는지 내부적으로 저장하고 value를 이용해서 끌어올 수 있다
    - 필드 자체적으로 상태를 기억하고 쓸 수 있다.

- input등의 자체 상태 기능을 그대로 유지하게 할 수도 있고 자체 상태 기능을 못쓰게 바보로 만들어 버릴 수도 있다.

- 제어되는 컴포넌트(Controlled Components)★★★★

### 제어되는 컴포넌트(Controlled Components)★★★★

- html에서 폼 요소의 상태가 저장되는 저장소가 있고, react의 상태가 저장되는 저장소가 있다.
- 이 두 저장소를 하나로 합쳐서 (input등의 상태를 없애버리고) 리액트 state를 “진리의 유일한 원천 (single source of truth)“으로 만들어 두 세계를 결합할 수 있습니다. 이렇게 하면 사용자의 입력에 따라 폼에서 발생되는 일을 React 컴포넌트 측에서 제어하게 됩니다. 이런 방식으로, React에 의해 제어되는 input 폼 요소를 “제어되는 컴포넌트” 라고 부릅니다.
- 인풋 텍스트에어리어 셀렉트 등을 화면에 그리게만 한다. 다르게 표시되게 만들고 싶다면 리액트의 상태를 바꿔줘야 다르게 표시된다.

```js
// 이렇게하면 제어되는 컴포넌트가 된다.
<input type="text" value={this.state.value} onChange={this.handleChange} /> 
```
- value prop에 문자열을 넘겨주면 제어되지않는 컴포넌트가 된다 

- [폼 예제-input에 숫자만 쓸수있게 하기](https://codepen.io/Shim-SoYoung/pen/BGWjqx)

- 원래 DOM에서는 input요소에는 인풋이벤트를 입력해야하는데 리액트에서는 그냥 `onChange만` 쓰면 된다.


### textarea 태그
### select 태그
[리액트-폼-셀렉트](https://codepen.io/Shim-SoYoung/pen/JeWGQb)


### 제어되는 컴포넌트의 대안책
제어되지않는 컴포넌트를 사용하려면 DOM객체를 가져와야한다.
...ㅠ


# State 끌어올리기
- 혼자읽어보세요. 넘 복잡해용
- 공유되는 상태가 필요할때는 부모에게 상태를 끌어올린다.
-여러 자식들이 공유하는 상태가 필요할때, 자식 ㄴ컴포넌트들끼리 통신할 때 상태를 끌어올린다.

# 합성(composition) vs 상속(inheritance)
- 리액트에서 컴포넌트간의 코드를 재사용 해야할 때는 합성을 사용하자.

```js
function WelcomeDialog() {
  return (
    <FancyBorder color="blue">
      <h1 className="Dialog-title">
        Welcome
      </h1>
      <p className="Dialog-message">
        Thank you for visiting our spacecraft!
      </p>
    </FancyBorder>
  );
}
```
- 위 코드가 있을 때 `FancyBorder` 아래의 `h1`, `p`는 자동으로 props.children이 된다.
- prop으로 element도 넘길 수 있다.(element도 값이니깐!)

### 특수화(Specialization)
### 상속은 쓰지 말자

