# 2018-09-10 월요일 HTML 3일차

# 1. agent style 초기화 = reset style
1. reset.css
    - 여백을 0으로 설정 후 진행
1. normalize.css
    - 여러가지 브라우저들이 비슷한 환경에서 시작할 수 있도록 여백, 폰트사이즈 등을 조절한 css

## box-style 
1. content-box(w/h+p+b+m)
1. border-box(w/h[p+b]+m)

## 단위(rem, em, px, vh, %)
1. document object model (DOM)
1. em : 상속받음. 2em일때 상속받은 크기의 2배
1. rem(root equal m) : 상속받지않음. 기준을 html의 폰트사이즈로 감.
    - 2rem : html의 폰트사이즈의 2배. (10px일 시에는 20px. 부모로부터 상속받지않고 무조건 html)

## font(1 2 3 4): family 설정 필수
1. 1.font-style : italic
1. 1.font-varient : small-caps (소문자와 대문자의 높이가 동일해진다. 자연스러운 대문자표현)
1. 1.font-weight: bold
1. 2.line-height : 1.2
1. 3.font-size: 12px
1. 4.font-family: 고딕체

## table reset 설명
1. tr(table row)
1. th(table head)
1. td(table data)
1. cell spacing의 여백을 삭제해주는 border-spacing
1. border-collapse : collapse를 해주면 border가 겹쳐지지않는다.


# 2. 본문 기본 스타일 설정

## a 선택자 : 순서를 꼭 지켜야한다. hover와 focus를 먼저 쓰면 link와 visited로 재정의 되기때문에 색이 덮힌다.
1. a:link
1. a:visited
1. a:hover
1. a:focus(active)

## 글꼴 설정
1. 웹폰트
    - 단점 : 웹폰트를 내려받는 시간이 걸릴 수 있다.
    - google web font, web font gallery ...
1. font-family: "Noto Sans KR", sans-serif;
    - noto sans kr의 글꼴로 렌더링하고 만약 이 폰트가 없으면 산세리프형식의 다른 글꼴을 사용한다

## @
- @ :선언

# 3. .member 마크업(3way)
1. flex
    - direction이 row 라면 메인축이  x축
1. float
    - 
1. inline/inline-block을 이용한 디스플레이 방법론.
    - inline : 코드에서 엔터(줄바꿈)을 하면 그 공백을 하나의 인라인 요소로 인식하기 때문에 인라인 사이에 공백이 생긴다.
        * 방법 1. 줄바꿈 없이 한줄로.
        * 방법 2. `<!-- -->`  주석 삽입
        * 방법 3. 부모요소에 font-size를 0으로 준다.
    - text-align: right를 준다.

# 4. Grid
1. 디자인이 그리드 기반으로 나와야 한다.
1. grid system

# 5. 가상선택자를 이용해서 디자인
1. after, before에 content: "";를 사용해서 구분 바를 삽입.

# 6. 구조선택자(**14번 북마크**)
1. li:nth-child(n+6) : 여러개의 li중에서 6번째로 시작하는 li부터 뒤까지 쭉 해당 스타일을 적용한다. : 6 이상
1. li:nth-child(-n+9) : 9 이하
1. nth-child(n+4):nth-child(-n+8) : 4이상 8 이하
1. nth-child(3n+1):nth-child(even) : 3개씩 그룹을 지어서 선택. (123, 456, 789) 중에 짝수(even)만 선택하겠다.

# 7. 숨김 콘텐츠(메인메뉴)
1. hidden : html5에서 새로 나온 기능. = display:none이라서 포커스가 잡히지 않는다. 접근성에 좋지 않음.
1. visibility:hidden;  : 화면에서만 가려짐. 별루
1. position: absolute; left:-9999em; :가장 많이 사용하지만 스크린리더기로 읽었을때 오류가 있기때문에 권장되지 않음.

1. width:1px, height: 1px, overflow:hidden : 
    * clip(top, right, left, bottom) : position absolute에서만 쓸 수 있다
    
```
포인트
1. display:inline/inline-block
2. 상속(inherit)
3. reset vs normalize 스타일 초기화
4. 웹폰트
5. 선택자
```

# 2018-09-11 화요일 HTML 4일차

# 1. 동적인 제어 (.menu-act) `바닐라 자바스크립트?`
- addClass()
- removeClass()

# 2. Gradient 
1. lenear-gradient
    - to bottom 위에서 아래로. 
    - to left : 오른쪽에서 왼쪽으로
    - -45deg : 45도
    - (-45deg, red, green) 45도 방향으로 빨간색, 초록색 그라디언트
    - (-45deg, red 0%, green 50%, blue 100%) : 0퍼센트 지점부터 빨간색, 50퍼센트 지점부터 초록색 100퍼센트 지점부터 파란색
1. gradient gallery로 검색하면 이쁜 예제 많음.
1. repeating-lenear-gradient 를 이용해서 스트라이프를 만들 수 있다.

# 3. border-radius
1. (left-top, right-top, right-bottom, left-bottom)
1. 완만한 모양의 모서리도 그릴 수 있음.
```
border-radius: 100px 0 0 0 / 50px 0 0 0 
좌측 상단에 완만한 모양의 모서리 생성
```


# 4. 윤곽체를 만들어보자 text-shadow: 1px 1px 0 #000; 
1. x축 1px
1. y축 1px 
1. 블러(흐리게) 처리
1. #000 그림자색상
1. 1px 1px 0 #000, 1px 1px 0 #ccc : 멀티 쉐도우 가능 
1. 그림자를 상하좌우로 1px씩 줘서 윤곽선처럼 만들 수 있다.


# 5. 색상 함수
1. #ffffff
1. rgba(255, 255, 255, 0.5)
1. hsla(90, 50%, 70%, 1)

# 6. line-height

# 7. 선택자 (nth-child)
1. .menu .sub-menu:nth-child(1) : 선택이 안됨
    - .menu .menu-item:nth-child(1) .sub-menu : 이게 옳은 선택자.(이해가 필요하당..)


# 8. sub-menu 나열하기
- 방법1. flex
    1. .sub-menu에 display:flex;
    1. width를 크게 준다 
    * BAD

- 방법2. inline-block
    1. .sub-menu li에 display:inline-block;
    1. .sub-menu에 white-space: nowrap; (줄바꿈 금지)

- 방법3. float
    1. .sub-menu li에 float
        - float를 설정하면서 붕 뜨게 된 박스가 p:a 를 주게되면서 높이가 잡힌다.

# 9. sub-menu 텍스트 앞의 bullet 
- before 가상선택자 사용
- icon font 사용 (웹폰트같은. font awesome)
- fontello


# 10. 동적 제어
- 헤드부분에 스크립터 제어문을 넣으면 파싱이 안 될 때도 있다. 그래서 body의 맨 마지막에 넣는걸 추천
- defer : 스크립트 실행 시점 설정. 
    * html5 defer async 구글링

- item.on(mouseover focusin) : 두가지 이벤트가 발생했을때
- 익명의 펑션은 위의 두가지 이벤트가 발생했을때 중괄호 안의 이벤트가 실행된다.
- $(this) 현재 객체에.

```
var subItem = $('.sub-menu a');
subItem.attr('class', 'fas fa-angle-left');
```



# 예습 : CSS animation 프로퍼티, form관련 프로퍼티 예습해보기
















@@ 난 여태 원시인처럼 코딩했구나,,