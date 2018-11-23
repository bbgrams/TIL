# React Router에서 사용되는 컴포넌트에 대한 간략한 설명

## `<BrowserRouter />`, `<HashRouter />`

- **Context API의 Provider와 유사한 역할**을 한다.
  - BrowserRouter의 경우 브라우저의 popstate 이벤트와 연동되어 있다.
  - HashRouter의 경우 브라우저의 hashchange 이벤트와 연동되어있다.
- 아래에 나오는 컴포넌트들은 전부 Context API의 Consumer와 유사한 역할을 한다. (즉, 상위 Router 컴포넌트와 연동되어, 상태를 받아오거나 상태를 바꿀 수 있다.)

## `<Link />`

- **`a` 태그로 렌더링되는 컴포넌트.** 클릭했을 때 주소 표시줄의 상태를 바꾸고, 페이지 전환을 일으킨다.
- `href` 역할을 하는 `to` prop을 통해 어떤 주소로 이동할지를 지정해줄 수 있다.
- 상위에서 BrowserRouter가 사용되면 `history.pushState`를 통해 주소를 바꾸고, HashRouter가 사용되면 `location.hash`를 바꾼다.

## `<Route />`

- `Route` 컴포넌트는 react-router의 핵심적인 구성요소로, 주소에 따른 **선택적 렌더링**을 할 때 사용된다.
- `path` prop과 주소가 일치할 때에만 렌더링된다.
- `component`, `render`, `children` prop을 통해 무엇을 렌더링할지 지정해줄 수 있다.
  - `component` prop에는 렌더링하고 싶은 컴포넌트를 넘겨줄 수 있다. 이 때, 여기에 주어진 컴포넌트는 라우팅과 관련된 여러 prop을 받는다. (`match`, `location`, `history`)
  - `render` prop에는 엘리먼트를 반환하는 함수를 넣어줄 수 있다. 이 때, 매개변수에는 라우팅과 관련된 여러 정보가 주어진다. (`match`, `location`, `history`)
  - `children` prop의 사용법은 `render`와 유사하나, 여기에 넣어준 함수에서 반환된 엘리먼트가 반드시 렌더링된다는 차이점이 있다. 애니메이션 등을 구현할 때에 사용되며, 보통은 잘 사용되지 않는다.

## `<Redirect />`

- **렌더링되었을때** 주소가 바뀌는 컴포넌트. `Link` 컴포넌트와 함께 주소를 바꾸는 데에 사용된다.
- `Link` 컴포넌트는 사용자가 링크를 클릭해야만 주소가 바뀌는 데 반해, `Redirect` 컴포넌트는 **마운트되는 순간** 주소가 바뀐다는 차이점이 있다.
- `from` prop과 `to` prop을 받을 수 있다.
  - `from` prop을 생략한 경우, 마운트되는 순간 바로 `to` 주소로 이동한다.
  - `from` prop을 넣어준 경우, 현재 주소가 `from`과 일치하는 경우에만 `to` 주소로 이동한다. 

## `<Switch />`

- 자식 노드에 Route, Redirect 컴포넌트가 있을 때, **처음으로** 주소가 일치하는 Route 혹은 Redirect **하나만** 동작하게 만드는 컴포넌트. 
- 여기서 '주소의 일치'란, 브라우저 주소표시줄의 주소가 Route 컴포넌트의 `path` prop, Redirect 컴포넌트의 `from` prop과 일치하는 것을 말하는 것이다. 