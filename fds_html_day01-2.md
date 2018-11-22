# 2018-09-06 목요일 HTML 1일차

# 웹접근성과 웹표준

##  1. 인터넷
1. 인터넷 서비스 : Telnet IRC e-mail Archie Usenet Gopher FTP **WWW**
1. WWW(World Wide Web)
1. HTML : 뼈대
1. CSS : 스타일링
1. java script : 스마트한 두뇌


## 2. 웹표준
1. W3C
1. 책 추천 [제프리 젤드만의 웹표준 가이드]

## 3. 웹접근성 Web Accessibility
1. 장애환경 : 시각장애(전맹, 저시력), 청각장애, 지체장애(절단 및 지체기능 장애), 뇌병변 장애
1. 환경에 대한 이해
    1. 다양한 Platform
    1. Cross Browsing
    1. SEO(Search Engine Optiomization) : 검색엔진최적화
    1. 저사양 또는 저속회선



## 4. HTML5
1. HTML의 탄생
1. DTD - S, T, F(프레임셋)
    1. t:호환성을 위한
1. 코딩 컨벤션 - 개발 규칙 (대소문자, 들여쓰기, 띄어쓰기, 특수문자 등등.. 코드의 일관성과 품질을 위해)
1. XHTML - HTML의 확장버전
    1. HTML 4.01의 재정의
    1. 모든 태그는 열었으면 닫아야한다.
    1. 모든 코드를 꼼꼼히 작성해야됨. 다들 귀찮아서 싫어함.
1. WHATWG(Web hypertext application technology work) - 애플, 모질라, 오페라
1. 2007년 W3C가 XHTML을 포기 선언. WHATWG에 참여.
1. HTML5 = HTML + CSS + JS의 합친 버전이라고 할 수 있다.
1. HTML4.01, XHTML1.0, HTML5의 차이점
    1. 새롭게 등장한 컨텐츠 모델.
        1. 인터랙티브 콘텐츠 : 사용자가 어떤 기능을 조작 할 수 있는 (상호작용) 콘텐츠
            1. `<a>, <img>, <input>, <object>, <video>` 
            1. 인터렉티브 콘텐츠 안에 인터렉티브 콘텐츠를 사용할 수 없다.(a는 여러그룹에 포함된다)
            1. 문법 검사하면서 허용, 비허용을 체크해봐야한다.
    1. 아웃라인 알고리즘
        1. HeadingsMap 확장프로그램을 이용해서 확인가능
        1. h1 : 대제목, h2 소제목.....
        1. `section, article, aside, nav`라는 태그가 생김
            1. 아웃라인을 ..따르는..섹셔닝 태그는 h태그를 꼭 써야함
        1. depth를 지켜가며 h태그를 써야하고, 뎁스 순서는 상위의 섹션태그를 따른다. 
1. HTML5의 API(application programming interface)
    1. web storage
    1. web sql database/indexed database
    1. application cache
    1. web workers
    1. web socket
    1. notific......
    1. file api
    1. geolocation
    1. device orientation
    1. speech input
    1. drag & drop
    1. 그 외 아주 많음
1. HTML 문법
1. 구글링을 많이 하세요


## 5. html snippet 사용자 설정 알아보세요.

## 6. 스니펫과 다른것들 단축키
1. html:5 라고 하면 세트가 쭈욱 나옴.
1. ctrl+shift+k : 커서가 있는 한 줄 삭제
1. `<meta charset="UTF-8">` 다국어 인코딩 지원한다는 뜻. euc-kr로 적으면 한국어만 지원하고 다른 언어는 깨짐.
    1. 에디터에서 지원하는 인코딩 타입도 UTF인지 확인해야함.

1. `<meta name="viewport" content="width=device-width, initial-scale=1.0">` 반응형 , 모바일사이트를 만들 때.
1. `<meta http-equiv="X-UA-Compatible" ` 호환성 보기 기능.
1. `content="ie=edge"> 가지고 있는 익스플로러중 최신 버전으로 진행
1. title : 정말 중요한 문구 넣기.
1. link:favicon 
1. div.container>header.header : 부모자식 형태로 생성
1. header.header+div.visual+.... 트리구조로 가능
1. 좌측 톱니바퀴  -바로가기키에서 원하는 키로 설정 가능
1. div.group.group$*3
    1.div.group.group${group$}*3
1. 블럭잡고 알트 아래방향키 하면 브럭한게 아래로 내려감
1. h1.logo>a[href="#"]>img
1. ul.member>li*>a[href="#"]    : 여러가지 메뉴 블럭잡고

1. 조합법은 에밋 신텍스 파트에 가면 있음

## 7. 마크업
1. 1단계. 디자인 시안을 보면서 구조를 생각해본다.
1. 2단계. 컨텐츠 중심의 마크업
    1. 성격이 서로 다른 컨텐츠끼리 나누거나 묶어주는 작업.
    1. 기본적인 3단구조 : 헤더-메인-푸터
    1. 4단구조 : 헤더 - 네비게이션-메인-푸터
1. 3단계. 시멘틱 마크업 : 의미있게
    1. 헤더의 영역 `<header>`
        1. 브랜딩영역
    1. 중심컨텐츠 영역`<main>`
    1. 슬로건 영역 `<article>`
    1. 푸터 영역 `<footer>`

1. 4단계. 네이밍(#id, .class) : 네이밍도 의미있게
    1. PascalCase : MainMenu
    1. CamelCase : mainMenu
    1. SnakeCase :main_menu
    1. CababCase : main-menu  (요즘 유행하는 케이스)
    1. BEM : 네이밍 관련 구글 키워드.

1. 중립적인 상황(ex.레이아웃을 위한 상황)에는 div를 사용

1. header, visual, main, slogan, footer를 왜 wrap | wrapper | container 로 감싸는 이유 : 5가지 구조태그의 width를 한번에 조절할 수 있다.

비단 width 뿐만은 아님.



## 8.CSS(cascading style sheet)
1. W3C에서 정식으로 권고 되지 않은 파트도 브라우저에서는 작동 할 수 있다.
1. 크로스 브라우징..은 똑같이 만드는게 아니라 모든 브라우저에서 동일한 작동을 하게 하는 것.(충격)
1.  .선택자 {선언부}
    1. selector{property : value;}
1. user agent style sheet : 여기서 user는 브라우저. 브라우저마다 유저 에이전트 스타일시트가 다르다.
    1. agent style 재정의 필요. 내가 추가한 스타일의 우선순위가 더 높다.
    1. 기존의 에이전트 스타일을 초기화하는것 : reset.css
1. 디자인에만 따라서 컨텐츠 순서를 마크업하지 말고, 
배치 관점이 아닌 컨텐츠 관점으로 마크업해야한다.

1. 컨텐트 박스 타입 : 마진, 패딩, 보더, width 모두 더해진 값이 박스의 넓이

1. 가운데정렬하는 방법은 flex, margin 0 auto, grid
    1. flex 명령은 내가 주고싶은 박스의 부모요소에게 줘야한다.
    1. flex 박스의 가장 큰 장점 : 자식요소의 width에 따라 유연하게 늘었다 줄었다 한다. 자식요소의 width가 넘쳐도 오류가 나지 않고 줄어들지만 이 때문에 오류가 날 수도 있으니 잘 알아보자.
    [플렉스](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

## 9. font size
1. em(equal m) : 부모가 상속해준 크기의 x배
    1. 1.5em : 부모가 10px이면 10의 1.5배

## 10. 벤더 프리픽스
1. webkit 크롬 사파리 오페라
1. -ms- 
1. -moz- 파이어폭스

## 10. 플러그인
1. 제플린

 ## 12. 높이설정
 1. 100vh: 보이는 브라우저의 화면의 100퍼
 1. 10vh : 10분의 1만큼의 크기



## ?? Q
1. 무조건 HTML5를 사용하는지?
1. flex 알아보기 : 





# 2018-09-07 금요일 HTML 2일차

## 1. WAI-ARIA
1. 옛날 div#header.. 이런식으로 짠 코드를 아리아를 이용해서 접근성을 구성하는 방법
    - 역할 모델인 role을 부여할수있다. 
    - header-banner, menu-navigation, contents-main, visual-group, footer-comentinfo(?)
    - div로 버튼을 만들었을때는 role="button"
1. 백그라운드로 이미지를 대신 할 때는 division태그에 aria-label"cocacoke" 라고 적어준다.



## 2. 배치에 관련된 모델
1. Box model
1. flex
1. float
1. position
1. grid

## 3. box-sizing
## 4. margin
1. 마진 값이 3개 들어가면 상/좌우/하
1. 마진은 투명한 영역
1. 마진 컬렉싱, 마진 병합 형상
    * 투명한 공간에서는 마진이 병합된다.

## 5. flex
1. 부모 요소에 flex를 주면 자식요소는 자동으로 items이 된다.
1. flex를 주면 자식요소가 자동으로 stretch 된다.
1. 자식요소의 width값이 부모요소의 컨텐츠영역보다 크더라도 알아서 크기가 줄어들며 꾸겨넣어진다.
1. flex-direction 에 따라 메인축, 교차축이 바뀐다 
    * justify-content 는 메인축 정렬
    * align-items 는 교차축 정렬
1. order
    * 자식요소에 주는 order
    * 기본값은 0
    * 맨 앞에 주고 싶을때는 0보다 작은숫자, -1로 주면 맨 앞으로 감.
    * 논리적인 형식을 유지하면서 디자인을 따를 수 있기 때문에 좋다.

1. align-self
    * 자식요소인 박스 하나만 교차축에서 움직임.

```
flex 자식요소의 크기를 조절해주는 프로퍼티들
1. flex-grow
    * 확대하는 배율을 결정해줌.
    * 기본값 0
2. flex-basis
3. flex-shirink
    * 축소하는 비율을 결정해줌
    * 기본값 1
* flex :3가지를 한번에 조절하고 싶을때 사용함.
```

## 6. Float
1. 붕 떠 있는 상태
1. left, right, none : 기본값은 none
1. inline 텍스트들이 밀린다.


* overflow: 

## 7. clear
1. float 된 것들을 해제한다.
1. 강제로 margin을 주어 투명한 공간을 만든다
    * 마진 병합 현상이 일어남
1. clear : left, right, both(둘다)
1. inline 요소에는 들어가지 않는다. block에만 사용 가능.
    
    * clearfix : 암묵적으로 float 된 형제를 clear 해준다.
    비어있는 가짜 요소를 삽입해서 clear 처리 하는 것.

## 8. 가상선택자
1. 하위 버전까지 생각하려면 콜론: 1개 
1. 상위 버전만 사용하려면 콜론 두개 ::
1. 눈에만 보이는 유령글자를 생성한다.
1. before 
    * 첫번째 자식요소를 추가 할 수 있다. css로 만드는 가짜 child. 무조건 first child로 생김
1. after
    * 마지막 자식요소를 추가 할 수 있다. 무조건 last child
1. before, after는 기본적으로 inline box여서 clear를 받을 수 없다. block으로 먼저 설정 후 가능

1. clearfix : 공통모듈.  float 때문에 문제가 일어나는 부모요소에 clearfix 클래스를 넣어준다.

## 9. 선택자
1. .container div 하위선택자

## 10. cascading 규칙
1. 선택자에 따라 파워가 다름
    - element  selector 1점
    - class selector 10점
    - id selector 100점
    - inline selector 1000점
1. 파워가 같을 경우에는 나중에 선언된 것이 적용.
1. 점수로도 계산할 수 있지만 계급도 있음.
    - id > class > element
    - class를 100개 써도 id는 이길 수 없다.

## ETC 
1. normal flow : 마크업 순서대로 배치되는 것
1. background-color:transparent; : 투명

## 8. inline 상자
1. width, clear 값이 먹지 않음.

---
# 마크업 순서 

## 1 콘텐츠 중심의 마크업 : 분석과 설계가 필수.
1. 마크업의 논리성. 논리적인 순서로 마크업
    * 논리 순서 : 좌-우, 상-하
    * 디자인 순서로 마크업 : 텍스트링크모음-로고-메뉴
    * 논리적 순서로 마크업 : 로고-텍스트링크모음-메뉴
1. 컨퍼런트 단위로 쪼개기.

## 2 시멘틱 마크업 : 의미를 잘 전달 할 수 있게 (h,,)
## 3 네이밍 : 최대한 의미에 맞게
---

### a11y-hidden

## 주요 네비게이션의 역할을 가지는 메뉴들을 <nav>에 넣음.

## 핸들링 하고싶은 곳에 네이밍을 해준다.
## li.menu-item에 마우스가 올라가있어야 하위메뉴가 뜨기때문에 menu-item에 네이밍을 따로 해주어야한다. 
* 아래 span.menu-item-text에만 주면 마우스가 하위메뉴로 내려갔을때 하위메뉴가 사라짐.

* span.menu-item-text는 링크가 걸리는게 아니기 때문에 span 사용.  span,li에는 키보드 포커스를 받지 않지만 키보드 포커스를 받을 수 잇게 만들 수 있다. = tabindex="number"
- 0 : 마크업한 순서로 접근하라 (권장)

## 배치부터 고민 후 데코레이션을 고민하라.
- 어느기법을 쓸지 고민하라.(float, flex, position, grid 중에)

### position을 이용한 배치
- position을 주면 block상태가 됨.
1. position : r
    * 상대배치
1. position : a
    * 노멀플로우를 벗어남. 제자리에서 붕 떠있음. 레이어가 됨
    * 컨텐츠 사이즈에 맞게 크기가 줄어들음. w나 h를 따로 정해주어야 함.
    * 자기보다 상위요소이면서 position이 static이 아닐때만 기준으로 삼음.
1. position : f
    * 뷰포트 기준.
1. position : sticky (r과 f의 조합같음.)


### z-index가 커야먄 상단으로 올라온다.
### polyfill : 브라우저별 CSS지원상황을 확인하고 지원이 안된다면 polyfill 키워드를 함께 검색해보자. 해당 기능을 제이쿼리로 구현해놓은 오픈소스가 있다. 