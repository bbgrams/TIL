# 2018-11-19
## 앞으로 배워볼 내용들
1. VS CODE => create-react-app
1. CSS 구조적 코딩 
    - BEM = > CSS 모듈
1. HTML5 history API (브라우저 내장기술) + React Router
    - 브라우저의 뒤로가기, 앞으로가기 버튼 기능
1. Container 컴포넌트 
1. Presontational 컴포넌트
1. SEO => SSR(server side rendering)/Next.js
1. + 리액트 공식문서의 내용들.


## JSX 더 알아보기

### React 엘리먼트의 타입 지정하기- 첫 글자는 대문자로 작성
대문자로 시작하는 타입은 해당 JSX 태그가 React 컴포넌트임을 가리킵니다.이 태그들은 같은 이름을 가진 변수를 직접 참조하도록 컴파일됩니다. 그러니까, `<Foo />`와 같은 JSX 표현을 사용하려면 `Foo가` 반드시 스코프 내에 존재해야 합니다.

```js
<div> hello </div>
```

태그의 첫글자가 대문자이면 리액트 엘리먼트로 인식한다.

```
엘리먼트 타입이 소문자로 시작한다는 것은 그것이 <div> or <span>와 같은 DOM 내장 컴포넌트라는 것을 뜻합니다. 이 컴포넌트들은 결과적으로 'div'혹은 'span'와 같은 문자열의 형태로 React.createElement에 전달됩니다. <Foo />와 같이 대문자로 시작하는 타입은 React.createElement(Foo)와 같이 이름 그대로 컴파일되며, 따라서 여러분의 JavaScript 파일에 정의되어있거나 혹은 다른 파일에서 import 된 컴포넌트여야 합니다.
```

## JSX에서 자식 다루기

### 문자열 리터럴
```js
<MyComponent>Hello world!</MyComponent>
```
여는태그와 닫는태그 사이에 있는 문자열은 props.children이 된다.

### 함수를 자식으로 사용하기
```js
// Calls the children callback numTimes to produce a repeated component
function Repeat(props) {
  let items = [];
  for (let i = 0; i < props.numTimes; i++) {
    items.push(props.children(i));
  }
  return <div>{items}</div>;
}

function ListOfTenThings() {
  return (
    <Repeat numTimes={10}> 
      {(index) => <div key={index}>This is item {index} in the list</div>} 
    </Repeat>
  );
}
```
1. `Repeat`의 props.children에는 `(index) => <div key={index}>This is item {index} in the list</div>` 라는 함수가 들어간다.
1. props.children에 함수가 들어갔기 때문에 ` items.push(props.children(i));` 이런식으로 사용할 수 있음.

### 진리값, null, undefined는 무시됩니다.
false, null, undefined, true 는 유효한 자식입니다. 그저 렌더링되지 않을 뿐입니다. 아무것도 그려지지 않는다.

- `falsy` 를 그리지 않는게 아니고 `false`를 그리지 않는것이다.(0, NaN은 그려진다.)




# 정적 타입 체크

1. 정적 타이핑
    - (실행 전) 컴파일 과정에 타입 검사
    - 실행 전에도 타입관련 버그를 발견 할 수 있다.
    - 하지만 사용이 어렵다.
    - C, C++, C#, swift, 코틀린
    

1. 동적 타이핑
    - 실행시간에 타입 검사
    - 실행 전에는 타입관련 버그를 발견하기 어려움
    - 루비, 파이썬

1. 정적 타입 체커
    - JavaScript에 `컴파일 과정 중 타입 체크 기능`을 추가한 확장 언어
    - 코드를 실행하기 전에 타입관련 버그를 찾아낼 수 있는 기술.
    - TypeScript(더 많이 씀), Flow(페이스북 개발)


# Ref(Reference 참조)와 DOM

1. prop으로 사용 할 수 없는 것 : key, `ref`

### 언제 ref를 사용해야 하나요?
1. 포커스, 텍스트 선택영역, 혹은 미디어의 재생을 관리할 때
    - DOM API 메소드로만 가능
1. 명령형 애니메이션을 발동시킬 때
1. 서드파티 DOM 라이브러리를 통합할 때

### Ref 생성하기
```js
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.myRef = React.createRef();
  }
  render() {
    return <div ref={this.myRef} />;
  }
}
```
React.createRef(); 라는 함수를 실행하면 객체가 생성되고 이 객체는 DOM 객체를..
DOM 객체를 가리키고 싶을 때 ref를 사용한다.(화살표 같은 느낌)
DOM객체를 가져오고싶은 div등에 붙인다.
```js
const node = this.myRef.current;
```
한번 연결시킨 뒤에는  current 속성을 이용해서 연결된 DOM node를 가져올 수 있다.

### Ref 사용하기
1. HTML 엘리먼트에 ref 어트리뷰트가 사용되면, ref의 current 속성은 DOM 엘리먼트 객체를 가리킵니다.
1. 클래스 컴포넌트에 ref 어트리뷰트가 사용되면, ref의 current 속성은 해당 컴포넌트로부터 생성된 인스턴스를 가리킵니다.
    - 클래스 컴포넌트를 생성하면 자동으로 인스턴스가 생성되고 this는 이 인스턴스를 가리킨다. 이 인스턴스를 가져올 수 있다.
1. 함수형 컴포넌트는 인스턴스를 가질 수 없기 때문에 ref 어트리뷰트 역시 사용할 수 없습니다.


# 게시판 실습하기
```
npx create-react-app my-app // npx : npm에 올라와있는 패키지를 다운로드&실행을 동시에 한다. 매번 새로운 패키지를 다운로드하기 때문에 최신버전을 다운받을 수 있다.
```
## create-react-app 
`src` 에 있는 파일들은 변환과정을 거치고
`public` 에 있는 파일들은 변환과정을 거치지않고 사용자들에게 전달된다.
- 익스플로러에는 전혀 적용이 안되고 엣지까지만 적용된다.
- 익스플로러 9, 10은 폴리필을 이용하여 적용 가능하다.
- 익스플로러 8 이하는 안된다.


- css 파일을 여러개로 나누어서 컴포먼트마다 하나씩.

# 2018-11-20

## 제어되지 않는 컴포넌트

### 기본값 지정하기

- input : `value` 를 직접 설정해주는 순간 제어되는 컴포넌트가 되기 때문에 기본 `value` 를 설정해주고싶다면 `defaultValue` 를 사용해주어야한다. (리액트의 기능)
    - 기본값을 넣어주면서도 제어되지않는 컴포넌트로 남겨두고 싶을때.
- `checkbox`, `radio` : `checked={true}` 로 설정해주면 제어되는 컴포넌트가 된다. `defaultChecked={true}` 로 제어되지않는 컴포넌트이면서 기본값이 체크되어있게 설정할 수 있다.
```js
<input type="text" defaultValue="ID" />
```


## 성능 최적화

### 상태 최적화 - 불변성

- setState()가 일어난 컴포넌트의 모든 자식 엘리먼트들을 새로 구축한다.
상태로부터 화면을 어떻게 그려야하는지 알아내야하기때문에 모든 render() 메소드를 다시 다 호출해본다.
- 위쪽에 있는 컴포넌트(App..)에서 상태가 자주 바뀌면 많은 자식의 render 메소드가 다시 호출되기때문에 느리다.
- props 와 state 는 모두 객체이고 이 두가지가 바뀌지 않았다면 화면을 새로 그릴 필요가 없다.
- state의 속성과 props의 속성이 바뀌지 않았따면 render() 메소드를 호출할 필요가 없다. => 이러한 최적화를 할 수 있다.

- render 함수와 함수형 컴포넌트는 순수함수여야한다.
- [![Edit 상태최적화 예제](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/xz3x93443p)\


- [![Edit 상태최적화 예제-참조가바뀌지않은](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/n0w9p0lqj4)
    - 상태 업데이트 버튼을 누르면 배열에 push해서 
이전상태에 들어ㅣㅇㅅ던 배열을 ㅏㄱ져와서 그놈하네 푸쉬. 푸시를 한 배열이 다음상태에 들어간다.

- 배열의 내용이 바뀌었는지 인식을 못하다니 문제가 있는걸가.

- 깊은 비교 : 내용 비교
- 다시 그릴 필요가없는 부분은 그리지않기위해 pure를 사용하는건데 화면을 다시 그릴 필요가 없는지 있는지를 검사하기위해서 깊은비교(비싼연산-연산이 오래걸린다.)을 한다면 최적화를 할 필요가 없어진다.
- 그래서 얕은비교를 사용하여 PureComponent는 아주 빠르게 작동한다.


- 불변성 : 내용이 변경되었을때 참조 역시 변경되면 그게 불변의 값이다. 

불변이 아닌 값(가변)이 변경되었는지 확인하려면 비싸다(연산이오래걸린다)

어떤 값이 내용이 바뀌면 무조건 참조가 바뀐다. 라고 하면 내용이 바뀌었는지 확인하려면 참조가 바뀌었는지만 확인하면 된다. => 그래서 깊은비교를 할 필요없이 참조만 바뀌었는지 확인할 수 있다.


react.component를 상속받으면 setState를 호출할 때무다 렌더메소드를 다 호출한다 => 비싸다.

내용이 바귀었을때만 렌더메소드가 호출되어 내용을 변경하고싶다 => 정말로 내용이 바뀌었는지(깊은비교)를 확인하려면

상태 안에 저장하는 값들을 불변한 값(값과 참조가 같이 바뀌는)인 것처럼 코딩을 하면 리액트는 얕은 비교 만으로도 빠르게 비교하고 그릴 수 있다.

- 배열이나 객체가 들어왔을 때는 꼭 복사해서 새 배열을 만들어서 참조를 바꾸고 진행하다.

- 불변성의 단점 : 매번 확인할 때마다 새배열이나 새 객체를 만들어야하기 때문에 속도가 느리고 메모리가 든다.

- 매번 설정해주기 번거로운 부분이 있어서 라이브러리를 많이 사용한다. 

#### 라이브러리

[immutable-js](https://facebook.github.io/immutable-js/)
    - 참조를 하면 자동으로 
    - List : 배열 같은
    - Map : 객체 같은
    - [repl실습](https://repl.it/@bbgrams/GaseousInnocentUpgrades)
    - 내장된 객체와 배열 메소드를 쓸 수 없고 라이브러리에서 설정한 메소드만 사용할 수 있다.

[immer](https://github.com/mweststrate/immer)
    - 내장된 객체와 배열 메소드를 쓸 수 있다.
    - 요즘 떠오르는 불변값 라이브러리


### 비교조정 피하기

일부 상황에서 컴포넌트를 업데이트할 필요가 없는 경우 `shouldComponentUpdate` 에서 `false` 를 반환하여 이 컴포넌트 및 하위에서 호출하는 `render()` 를 포함한 전체 렌더링 프로세스를 스킵할 수 있습니다.

`PureComponent에` `shouldComponentUpdate` 라는 라이프사이클 훅이  내장되어있다.

## 비교조정

이전에 그렸던 것과 다음에 그려야할 것을 비교해서 수행해야할 것만 수행하는 것

- O(n^3), O(n^2) : 연산이 느림
- O(n), O(n^log) : 연산이 빠름

### 비교 규칙
1. Element Type 다른타입의 엘리먼트인 경우
1. key

두가지를 비교한다. 위의 두 가지가 바뀌면 더 이상 비교를 수행하지않고 통째로 새로 그린다.

### 비교 알고리즘

1. 다른 타입의 엘리먼트인 경우

    트리를 버릴 때, 이전 DOM 노드들은 모두 파괴됩니다. 또한 컴포넌트 인스턴스의 `componentWillUnmount()` 라이프 사이클 훅이 실행됩니다. 새 트리가 구축될 때, 새 DOM 노드들이 DOM 안에 삽입됩니다. 그에 따라 컴포넌트 인스턴스의 `componentWillMount()` 훅이 실행되고, 그 다음 `componentDidMount()` 훅이 실행됩니다. **이전 트리에 연결되어 있던 모든 state가 유실됩니다.**


1. 같은 타입의 DOM 엘리먼트인 경우

    같은 타입의 두 React DOM 엘리먼터를 비교할 때, React는 양쪽의 속성을 살펴본 뒤 같은 것들은 유지시키고 변경된 속성만을 갱신합니다.
    하위 요소에 대해서 똑같은 작업을 수행한다.


1. 같은 타입의 컴포넌트 엘리먼트인 경우
    
    라이프사이클 훅ㅇ......
    state는 날라가지않는다.


1. 키

    같은 자료이면 같은 키를 유지해야한다. 키가 바뀌면 다른 자료로 인식한다.
    
    키가 변경되면 state가 날라간다.

    상태를 다 날려버리거나 라이프사이클 훅을 다시 실행하고싶을 때 키 값을 변경해서 진행할 수 있다.

1. 엘리먼트 타입이나 키가 바뀌면 상태가 다 날라간댜!



# 2018-11-22 
## Context
### context 보기 전에 합성과 상속을 다시보자
- 이거 이해 못했씀.ㅎㅎㅎㅎ
- 최상단인 App 컴포넌트에다가 만드는것보다 
- 컴포넌트가 많아지고있다 => 복잡
- PostForm은 글쓰기와 수정을 위한 폼

### Context

앱의 여러 부분에서 공유되어야 하는 정보를 Context로 다룬다.
앱 전역에서 공유되어야하는 정보를 다루고 싶을 때.


Provider가 정보를 내려주면 밑에있는 Consumer가 받아서 쓸 수 있다.
```js
// Context를 사용하면 prop을 일일이 엮어주지 않고도
// 컴포넌트 트리의 깊은 곳에 값을 넘겨줄 수 있습니다.
// 테마에 대한 context를 만들어줍시다. ("light"를 기본값으로 합니다.)
const ThemeContext = React.createContext('light'); // 객체 생성.

class App extends React.Component { 
  render() {
    // Provider를 사용해서 현재 테마를 트리 아래쪽으로 넘겨줍시다.
    // 어떤 컴포넌트든 이 값을 읽을 수 있습니다. 아주 깊은 곳에 위치해있더라도 말이죠.
    // 아래에서는, "dark"라는 값을 넘겨주었습니다.
    return (
      // 정보를 내려주고싶은부분을 provider로 감싸준다.
      // value 값을 내려준다.
      <ThemeContext.Provider value="dark">
        <Toolbar />
      </ThemeContext.Provider>
    );
  }
}
```

```js
// 이제 더이상 중간 계층에 있는 컴포넌트에서
// theme prop을 넘겨줄 필요가 없습니다.
function Toolbar(props) {
  return (
    <div>
      <ThemedButton />
    </div>
  );
}

function ThemedButton(props) {
  // 테마 context를 읽어오려면 Consumer를 사용하세요.
  // React는 가장 가까운 Provider를 찾아서 그 값을 사용할 것입니다.
  // 이 예제에서, theme 값은 "dark"가 됩니다.
  return (
      // 버튼을 반환하는 함수를 적어준다
      // value로 내려준 dark가 함수의 매개변수로 들어와서 함수가 실행된다.
    <ThemeContext.Consumer>
      {theme => <Button {...props} theme={theme} />}
    </ThemeContext.Consumer>
  );
}
```


### API

```js
const {Provider, Consumer} = React.createContext(defaultValue);
```
Provider, Consumer 컴포넌트를 반환한다.
여러개의 컨텍스트를 두고 쓸 수 있지만 연결된 Provider, Consumer만 받아올 수 있다.
`defaultValue` 인수는 오직 상위에 같은 context로부터 생성된 Provider가 없을 경우에만 사용됩니다. 이 기능을 통해 Provider 없이도 컴포넌트를 손쉽게 테스트해볼 수 있습니다. 주의: Provider에서 undefined를 넘겨줘도 Consumer에서 defaultValue를 사용되지는 않습니다.
provider가 없고 consumer만 있을 때 사용 가능. 기본값으로 쓸 수 있다.(defaultValue에 dark를 넣어놓으면 provider가 없이 consumer 만 썼을 때 dark 테마가 유지된다.)

### Provider
value로 값을 넘겨주어야한다.


### Consumer
```js
<Consumer>
  {value => /* render something based on the context value */}
</Consumer>
```
render되는 부분엔 내가 그리고 싶은 내용을 넣어준다

`shouldComponentUpdate` 의 영향을 받지 않으므로 중간에 렌더링이 막혔다 할지라도 provider에서 내려주는 value값이 바뀌면 다시 렌더링된다.

- 등호 3개,등호2개, `object.is` 복습하기

- [![Edit 리액트-Context 사용예제 1](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/l5wl85x42z)
- [![Edit 리액트-Context 사용예제 1 - render안에 객체를 넣지 않는 예제](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/ykyp7wx7jz)
- [![Edit 리액트-Context API 예제 - 메뉴선택 -오류있음](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/82zx2k3jz2)

### 값이 변하는 context 

context에 내려줄 값을 상태에 담아야한다.

그떄그때 다른 값을 내려주고시싶때는 **provider를 렌더링해주고있는 컴포넌트에다가 상태를 두고** 그때 그때 상태를 바꿔주면 된다.
그리고 그 상태를 provider에 내려준다.


상태를 바꾸는 함수도 context를 통해서 내려주
아래 컴포넌트에서 context 값을 바꿔줄수 있을까.

객체에 함수를 넣어서 내려주자.

```js
// createContext에 넘겨주는 기본값의 모양이
// 실제 consumer에서 사용되는 값과 일치하도록 신경써주세요!
export const ThemeContext = React.createContext({
  theme: themes.dark,
  toggleTheme: () => {},
});
```
기본값으로 내려줄 내용

```js
import {ThemeContext} from './theme-context';

function ThemeTogglerButton() {
  // ThemeTogglerButton 컴포넌트는 theme 뿐만 아니라
  // toggleTheme 함수도 받고 있습니다.
  return (
    <ThemeContext.Consumer>
      {({theme, toggleTheme}) => ( //매개변수도 분해대입으로 쓸수있다.
        <button
          onClick={toggleTheme}
          style={{backgroundColor: theme.background}}>
          Toggle Theme
        </button>
      )}
    </ThemeContext.Consumer>
  );
}

export default ThemeTogglerButton;
```

1. provider에 내려보낼 내용을 상태에 저장할수있다.
1. provider에 객체를 내려보내줄수있다


 내려보낼 객체에 따라서 


### 라이프사이클 메소드에서 context에 접근하기

### 주의사항

Context는 consumer를 다시 렌더링해야하는 시점을 결정하기 위해 값의 참조가 동일한지를 비교하기 때문에, provider의 부모가 렌더링될 때 consumer가 불필요하게 다시 렌더링되는 문제가 생길 수 있습니다. 예를 들어, 아래 코드는 Provider가 다시 렌더링될 때 모든 consumer를 다시 렌더링시키는데, 이는 value에 매번 새로운 객체가 넘겨지기 때문입니다:


이 문제를 회피하려면, value로 사용할 객체를 부모의 state에 저장하세요:


## Fragments

Fragments를 사용하면 DOM에 별도 노드(`<div>`)를 추가하지 않고 자식 목록을 그룹화할 수 있습니다


## Portals
`쌓임 맥락.  스택킹 콘텍스트`

app은 div#root 안에 존재한다. root 바깥에 있는 DOM 노드에 그릴 수 있다. 

portals는 부모 컴포넌트(root)의 DOM 계층 외부에 존재하는 DOM 노드로 자식에 렌더링하는 일급 방법을 제공합니다.

모달, 팝업 등에서 사용한다.

root 바깥에 모달에 그려질 수 있다.


```js
<div id = "root">
  <App />
</div>
<div id ="portals">
</div>
```
```js
render() {
  // React does *not* create a new div. It renders the children into `domNode`.
  // `domNode` is any valid DOM node, regardless of its location in the DOM.
  return ReactDOM.createPortal(
    this.props.children, // 1. 요기 있는 내용이
    domNode, // 2. 요기 안에 그려진다.
  );
}
```
[리액트 - Portals 예제 eng](https://codepen.io/Shim-SoYoung/pen/wQyNaL) 


### Portals를 통한 이벤트 버블링
portal 내부에서 시작된 이벤트는 DOM 트리 에서 조상이 아니더라도 React 트리 에 있는 조상에 전달됩니다. 다음 HTML 구조를 가정해봅시다.

DOM에서는 다른 구조에 있는 노드이더라도 리액트상에서는 자식노드이기 때문에 B에 걸어놓은 onClick이 C를 눌러도 작동할 수 있다.

```js
react : A > B > C
html : root > A > B , portar > C
```

### 추상, 구상





# 2018-11-23

## 고차 컴포넌트(Higher-Order Components)

컴포넌트
- 리액트 클래스를 상속받은 컴포넌트
- 엘리먼트를 반환하는 함수형 컴포넌트

고차 컴포넌트는 컴포넌트로 사용할 수 없다. 컴포넌트를 만들어낼때 사용된다.

### 횡단 관심사를 위해 HOC 사용하기.

여러가지 페이지에서 공통적으로 사용되는 기능.(ex. 로그인)

```js
const CommentListWithSubscription =  withSubscription(
  CommentList,
  (DataSource) => DataSource.getComments()
);
```
컴포넌트(CommentList)와 업그레이드 할 설정((DataSource) => DataSource.getComments())을 넘겨서 컴포넌트(CommentListWithSubscription)를 새로 만들어낸다.

```js
// This function takes a component...
function withSubscription(WrappedComponent, selectData) {
  // ...and returns another component...
  return class extends React.Component { // 익명 클래스 컴포넌트가 반환된다.
    constructor(props) {
      super(props);
      this.handleChange = this.handleChange.bind(this);
      this.state = {
        data: selectData(DataSource, props)
      };
    }

    componentDidMount() {
      // ... that takes care of the subscription...
      DataSource.addChangeListener(this.handleChange);
    }

    componentWillUnmount() {
      DataSource.removeChangeListener(this.handleChange);
    }

    handleChange() {
      this.setState({
        data: selectData(DataSource, this.props)
      });
    }

    render() {
      // ... and renders the wrapped component with the fresh data!
      // Notice that we pass through any additional props
      return <WrappedComponent data={this.state.data} {...this.props} />;
    }
    // 업그레이드 된 새로운 컴포넌트에서는 인수로 되
    // 고차함수에서 첫번쨰 인수로 컴포넌트가 들어옴(commentList, )
    // 컴포넌트를 받아서 기능을 추가해서 다시 그려준다.
  };
}
```

HOC는 입력받은 컴포넌트를 수정하지도, 상속받지도 않는다.

대신 HOC는 원래의 컴포넌트를 다른 컴포넌트로 감싸는 식으로 합성한다.

HOC는 부작용을 갖지 않는 순수함수이다.



### 원래 컴포넌트를 변경하지 마세요. 합성을 사용하세요.

새로운 컴포넌트를 만들고, 기능을 추가하고, 컴포넌트를 다시 그려주는 방식을 사용하라.


### 관례: HOC와 무관한 prop은 감싸진 컴포넌트에 넘기세요.

### 관례: 합성을 최대한 활용하세요.

```js
// HOC의 가장 일반적인 모양
// React Redux's `connect`
const ConnectedComment = connect(commentSelector, commentActions)(CommentList);
// connect : 고차 컴포넌트를 반환하는 함수
```
connect 첫번쨰 괄호까지 실행되면 고차컴포넌트가 튀어나온다. 그 함수의 인수를 CommentList를 주면 업그레이드된 컴포넌트가 튀어나온다.

connect를 사용하여 단일 인자를 받는 HOC를 만들어낸다. 단일 인자를 받는 HOC는 함수 합성이 쉬우므로

```js
const enhance = C => withRouter(connect(commentSelector)(C))
```

### 관례: 원활한 디버깅을 위해 displayName도 감싸주세요

고차함수의 단점 : 계층이 복잡해진다.

```js
WithUser.displayName = 'WithUser(!!!)' 
// 개발자도구에서 알아보기 쉽게 displayName에 이름을 넣어줄수있다. 리액트만의 기능
```

### 주의사항

1. HOC는 단 한번만 적용되게 만들어야한다.
    - render() 메소드 안에서 HOC를 사용하면 렌더링될때마다 새로운 컴포넌트가 만들어지고...

1. Ref는 전달되지 않는다.
    - Ref가 아닌 다른 이름(innerRef)으로 Ref객체를 받아서 아래로 넘길 수 있다.



## 브라우저 히스토리 조작하기

[브라우저 히스토리 조작하기](https://developer.mozilla.org/ko/docs/Web/API/History_API)

- 브라우저는 조작 내용을 history stack에 저장한다. 

- SPA(Single Page App) : html파일 한개만으로 페이지를 조작하는것.

- MPA(Multiple Page App) : html파일 여러개를 가지고 조작하는것


### 히스토리 엔트리의 추가 및 변경

직접 history stack에 push를 할 수 있다.

1. pushState()

```js
var stateObj = {foo : "bar"}; 
history.pushState(stateObj, "page 2", "bar.html");
```
주소표시줄에 표시되는 주소를 바꿀 수 있다.
뒤로가기 버튼을 누르면 바뀌기 전 주소로 돌아간다

1. undo, redo
- 스택을 두 개 두고, undo 한 A를 2번째 스택에 넣고 redo하면 2번쨰 스택의 A를 꺼내서 첫번째 스택에 다시 넣는다.

1. `pushState()`, `popState()`, `hashState()`를 이용해서 리액트로도 뒤로가기 앞으로가기 등의 기능을 갖는 페이지를 만들 수 있다.


### 코드펜 실습
[pushState](https://codepen.io/Shim-SoYoung/pen/MzVXmy)



## 리액트 라우터 ROUTER (v4)

- v3과 v4가 많이 다르다.

1. "react-router-dom"

    - Router : provider과 비슷한 느낌
    - Route, Link : consumer와 비슷한 느낌

    - <link> 컴포넌트를 쓰면 <a> 태그로 변환된다. : preventDefault()하고 pushState()를 한다

```js
import React from "react";
import { BrowserRouter as Router, Route, Link } from "react-router-dom";

function BasicExample() {
  return (
    <Router>
      <div>
        <ul>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/about">About</Link>
          </li>
          <li>
            <Link to="/topics">Topics</Link>
          </li>
        </ul>

        <hr />

        <Route exact path="/" component={Home} />
        <Route path="/about" component={About} />
        <Route path="/topics" component={Topics} />
      </div>
    </Router>
  );
}

function Home() {
  return (
    <div>
      <h2>Home</h2>
    </div>
  );
}

function About() {
  return (
    <div>
      <h2>About</h2>
    </div>
  );
}

function Topics({ match }) {
  return (
    <div>
      <h2>Topics</h2>
      <ul>
        <li>
          <Link to={`${match.url}/rendering`}>Rendering with React</Link>
        </li>
        <li>
          <Link to={`${match.url}/components`}>Components</Link>
        </li>
        <li>
          <Link to={`${match.url}/props-v-state`}>Props v. State</Link>
        </li>
      </ul>

      <Route path={`${match.path}/:topicId`} component={Topic} />
      <Route
        exact
        path={match.path}
        render={() => <h3>Please select a topic.</h3>}
      />
    </div>
  );
}

function Topic({ match }) {
  return (
    <div>
      <h3>{match.params.topicId}</h3>
    </div>
  );
}

export default BasicExample;
```

1. ` <Route exact path="/" component={Home} />` : path가 `/`와 같다면 `{Home}`을 그려라.

1. match prop을 받고 match prop에는 여러가지 정보가 들어있다.

1. <BrowserRouter />, <HashRouter /> 
    - 둘 중에 한가지로 전체를 감싸주어야한다.

1. `<Redirect />` 
    - 리다이렉트 컴포넌트를 그리는것만으로 주소가 바뀐다. 화면에 그리기만해도 주소가 바뀐다.
    - 부작용을 일으키는 컴포넌트
    - 마운트 되는 순간 주소가 바뀐다.
    - 주소를 바꿔주어야 하는 시점(사용자가 버튼을 클릭하지않더라도 페이지를 바꿔주어야하는경우(로그인 했을 때, 게시글을 올렸을 때, 로그아웃 했을 떄 등..))에 사용한다.

1. [리액트 라우터 실습 - 가짜 게시판 만들기](https://codesandbox.io/s/vmv30n2pr3)

1. 브라우저의 주소표시줄이라는 상태를 다루는 라이브러리이다.

1. 사용자가 불편하지않게 즐겨찾기(북마크)를 할만한 페이지에는 모두 각자 다른 주소가 붙어있어야 한다

1. `Route`는 `if`처럼 동작하지 `if else` 처럼 동작하지 않는다.

1. `Route` 를 여러개 적어주면 같은 주소에서 여러개의 컴포넌트가 출력된다.

1. `switch` 라는 컴포넌트를 둘러주면 if else처럼 동작하게 할 수 있다.

1. switch 로 둘러주지 않았을 때
    - <Route component={NotFound} /> 처럼 path를 설정해 주지 않으면 모든 페이지에서 해당 페이지가 출력된다.

1. switch 로 둘러주었을 때
    - <Route component={NotFound} /> 잘못된 주소에 갔을 때만 해당 페이지가 출력된다.

1. switch 안에 Route를 입력할 때는 순서를 신경써서 써주어야한다 (위에서부터 동작하기떄문에-if else처럼)

1. 구체적인 주소를 쓸 때 위쪽에서 먼저 설정해주어야 한다.






 vscode에서 파일 열기 : ctrl + P 