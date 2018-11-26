# 2018-11-26 
# CSS 방법론

# 스타일을 설정하는 방식 두가지
1. BEM + SCSS : PostList
1. Adding CSS Modules : PostForm

## BEM(Block Element Modifier)

1. [[CSS방법론] SMACSS, BEM, OOCSS](http://wit.nts-corp.com/2015/04/16/3538)
1. class 이름을 짓는 법
1. 밑줄이나 하이픈을 써서 계층 구조를 나타낸다.
    - .header__navigation‐‐secondary과 같은 class를 사용한다
1. ID는 사용할 수 없고 class명만 사용할 수 있다.
1. BEM을 쓴다는것 :  클래스명으로 그 부분에 역할과 책임을 나타내고싶은것이다. => 되도록이면 한 요소에 클래스이름을 더럽히고싶지않은?? 공유되어야하는 스타일은 mixin으로 정의되는게 선호하는 방식이다.



### Modifiers

1. 어떤 element의 어떤 상태에 따른 스타일을 설정해주고 싶을 떄
    - `.login__id-input`
    - `.login__id-input--dup` 아이디가 중복되었을때의 인풋박스 스타일


### 리액트에서의 Block = Component
1. 컴포넌트명으로 시작 `.PostList` 



## SCSS SASS

[Sass Basics](https://sass-lang.com/guide)
- `npm install node-sass`

### Variables 변수

### import
1. `@import 'reset;`
    - import 된 css 파일이 그 자리에 들어온다.
    - 기존의 css는 `파일`을 불러오기 때문에 시간이 걸렸는데
    - 여러 파일에서 공유해야하는 변수를 한 파일에 작성하고 import하는 방식으로 사용한다.

### Mixins
1. 함수같은 느낌
1. 재사용 하고싶은(공유하고싶은) 코드뭉치들을 묶어놓고 재사용할수있다.
```scss
@mixin transform($property) { // $property가 매개변수
  -webkit-transform: $property;
  -ms-transform: $property;
  transform: $property;
}

.box { @include transform(rotate(30deg)); } // rotate(30deg)가 인수로 들어간다.
```

## Adding CSS Modules
기술이 도입된지 얼마 되지 않음.
- `[name].module.css` 로 파일 명을 설정해야만 한다.
- **자동으로 유일하고 식별 가능한 클래스이름을 만들어준다**
    - `[filename]_[classname]__[hash]
- 이름 충돌을 걱정할 필요 없이 여러 파일에서 같은 이름을 사용하게 해준다.(자동으로 변환되기 때문에)
- BEM기법의 하이픈을 쓰면 대괄호 표기법을 써야하므로 약간 불편하다 => CamelCase로 사용하면 점표기법으로 사용할 수 있다.




## Mobile First
- 모바일 버전을 먼저 맞추는 것. (추천)


## 기타
- 특정 컴포넌트와 관련된 같은 이름의 스타일시트를 따로 만들어보자.
- SCSS로 BEM을 쓴다.
- 여러 시트에서 공유 될 변수나 스타일은 common 스타일시트에 작성하자.


## -
###  editPostForm과 newPostForm의 스타일이 아주 조금 다를 때 어떻게 해야할까
- prop을 주어서 할 수 있다.


# UI FrameWork UI 프레임워크
- 스타일이 입혀져있는 컴포넌트가 미리 만들어져있고 이걸 가져다가 쓴다.

## semantic-ui

[시멘틱유아이](https://semantic-ui.com)
[시멘틱유아이-리액트](https://react.semantic-ui.com/)



## 부트스트랩

[부트스트랩](https://getbootstrap.com/)
[부트스트랩-리액트](https://reactstrap.github.io/)


# 스토리북
[스토리북](https://storybook.js.org/)

컴포넌트 데모 페이지

```js
cd my-react-vue-angular-app
npx -p @storybook/cli sb init


npm run storybook
```

컴포넌츠 폴더 안에서 스토리북을 작성할 수 있다. => Loading stories dynamically

```js
// 해당 소스를 config.js에 붙여넣으면 컴포넌트 파일 자체로 데모페이지를 만들 수 있다.
import { configure } from '@storybook/react';

const req = require.context('../src/components', true, /\.stories\.js$/);

function loadStories() {
  req.keys().forEach(filename => req(filename));
}

configure(loadStories, module);
```

- 통신을 하는 코드가 있는 컴포넌트는 테스트 할 수 없다.
- 부작용이 없는 코드만 테스트 진행