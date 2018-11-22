# 2018-09-13 목요일 HTML 5일차

## 1. visual 영역 만들긩 

### background 삽입
- multi background : 먼저 선언한 bg image가 가장 가장 위로 깔린다.
- 순서가  중요*
- 그 순서에 따라reapeat도 설정된다.
- attachment : fix / 배경 고장
-  background : yellow url("images/bg_flower.png") no-repeat 50% 0 / 500px 200px fixed;
    * (yellow 배경색, bg_flower.png 배경이미지, 반복없음, 50% 위치 / 500px의 사이즈, fixed)
- background 대표속성으로 멀티 백그라운드를 주려면 색상을 설정하면 안된다.
    * 배경은 반드시 따로 설정해야함.( background 속성 다음에 설정 )
- background 대표속성(단축표기법)은 bg-color가 기본적으로 투명으로 설정되어있다.

### css animation
1. 시나리오 먼저 작성
    1. 애니메이션 이름 textAni
    1. 내가 이 애니메이션에 어떤 효과를 주고싶은지.
        1. 텍스트 이동 : 왼쪽상단(0,0) → 오른쪽 하단(400px, 75px) -  padding, p:a
        1. 텍스트 크기 : 12px → 24px -  font size OR transform scale(이번예제에서는 좋지않음)
        1. 텍스트 투명도 : 0.2 → 1  - color : rgba()
    1. @keyframes : 이제부터 애니메이션을 선언하겠다는
        1. from{} / 0%{} : 시작하는 선언 블록
        1. to{} / 100%{} : 종료하는 선언 블록 

1. animation과 transfore, scale, translate, rotate 를 이용하여 이동하는것이 성능상 좋다.


---
1. 꽃 시나리오
    1. 애니메이션 이름 flowerAni
    1. 애니메이션 반복 
        - animation-iteration-count : 숫자를 적으면 그 횟수만큼 동작한다. 또는 infinite
    1. 애니메이션의 진행 방향
        - animation-direction: alternate 역방향 

1. Animation  대표속성(단축표기법)
    1. 선언 순서는 상관없음
    1. 값과 값 상태를 띄어쓰기로 구분
    1. name, duration은 필수값
    1. duration 1s,  delay 1s로 둘다 똑같을때, duration은 필수값이기 때문에 먼저 선언된 (n)s를 duration으로 인식한다.
    1. ease in 느리게 빠르게
    1. ease out 바르게 느리게
    1. ease in out 느리게 빠르게 느리게

## Transition
1. 시작하는 박스에 설정
1. background, border-radius가 1단계적으로 바뀌는건 가능.
1. border-radius가 둥그랬다가 네모였다가 세모였다가....등등등 하는거는 transition으로 불가능. animation으로 가능
1. property에 all이라고 적으면 box1과 box1:hover에 적용되는 모든 변화가 선택된다.
1. `css shape 구글링`







# 2018-09-14 금요일 HTML 6일차

1. 로그인 `<section>`
    1. `<form>` 
        * form 태그는 필수속성이 있음.
            * `[action= "보낼 서버"], [method="GET", "POST"]`
        * `<form>` 태그 밑에는 필수로 `<fieldset>`을 데리고 다녀야함
        * div: 범용 그루핑태그, fieldset : 폼서식 전용 그루핑태그
        * 필수요소, 선택요소를 따로따로 fieldset으로 묶는다
        * `<fieldset>`으로 묶은 세트의 목적을 `<legend>`로 명시한다
    1. input과 label
        * input의 id값을 `for=""`에다가 넣으면 두개가 묶임
        * name 서버로 내용을 보낼 때, 데이터가 name="" 에 담겨서 전송된다. 
        * required : 필수 입력 서식일 경우 추가(아이디,비밀번호)
        * size : 20으로 설정하면 20글자만큼의 길이가 설정된다.


    1. button[type="submit"].btn-login


    1. .login 디자인
        1. .login(배경색-주황, 상자 그림자)
        1. .login-heading(글자색상, 글꼴굵기, 들여쓰기-10px)
        1. .login-form(margin-10px, 둥근모서리-5px, 배경색-white, padding-10px, )
        1. .user-id, .user-pw
            * label : (font-size:4em) 최대 글자가 4글자이기때문에 4em으로 설정한다.
            * input : w-100px, h-22px
        1. 


        * radial-gradient(circle at left top) : 원형그라디언트 왼쪽에서 위로


1. dl dt dd : 용어 정의 태그
    1. 이름과 값이 있는 정보
    1. dt : title
    1. dd : 설명
    1. dl 내부의 태그들을 div로 묶을 수는 있지만 연관된 정보가 있는 세트만 묶을 수 있다.
    




[폼 액션 서버url 테스트](https://formspree.io/)
[form demo](https://www.miketaylr.com/pres/html5/forms2.html)
[find me my ip](https://bestvpn.org/whats-my-ip/)
[대한항공-접근성 최고](https://kr.koreanair.com/korea/ko.html)



# 2018-09-17 월요일 HTML 7일차

1. dd 안에 있는 이미지가 인라인요소기 때문에 아래 여백이 생긴다. 
    * img를 float:left 하거나 display:block 설정해줌.

1. div:not(:nth-child(odd))
    * 홀수번째가 아닌(:not)  = 짝수(even)


1. vertical-align
    - line-height 안에서의 bottom, top, middle
    - height:100px 일떄 line-height가 50이면 100px의 높이 안에 50px짜리 높이가 두 줄이 들어갈 수 있다.

1. 메인 게시판-공지사항,자료실 
    1. 공지사항
    1. 공지사항 목록
    1. 더보기
    1. 자료실
    1. 자료실 목록
    1. 더보기


1. time 현재 시간을 표현하는 태그
    - datetime이라는 값을 꼭 가져야함.
    - "연월일T시분초"  T로 구분


1. .board [class$="list"] : 속성선택자
    * .board의 자식요소 중 class값이 list로 끝나는 요소들을 모두 
    
1. 말줄임
    * white-space:wrap :: block성질의 상자에만 사용 할 수 있다. 개행 금지.
    * overflow:hidden :: 제목a태그(inline-block) 밑에 약간의 공백문자가 생긴다. 
        * 공백을 없애려면 inline 성질이 업서야하므로 block상자로 변경.


1. 반응형에서 쓸 수 있는 calc()
    1. calc(100% - 80px)  :: -연산자 양옆에 꼭 공백을 주어야함.



1. js event
    * click
    * mouseover
    * mouseout
    * focus
    * focusin



# 2018-09-18 화요일 HTML 8일차

## 웹카페 새소식 마크업 순서
1. 새소식
1. W3C사이트가 리뉴얼 되었습니다 (헤드라인)
1. 날짜
1. 기사 본문
1. 썸네일
1. 더보기



## `figure - figcaption `
## article
    * section과 성질이 비슷하다. (1장1절)
    * 블로그에 매일매일 글을 포스팅할때 완결된 하나의 정보에는 article을 쓴다.
    * 해당 웹카페 페이지에서는 리뉴얼됐다는 하나의 완결된 신문페이지 이기때문에 article 사용
    * article 안에 footer를 넣을 수 있다. = article영역의 마무리라는 뜻

## a태그로 article부분을 묶을때는 인라인요소가 블럭요소를 감싸는것이기 때문에 초점오류가 날 수 있다. 꼭 디스플레이를 block으로 설정

## 인터렉티브 컨텐츠 모델 안에는 인터렉티브 컨텐츠 모델을 넣을 수 없다.
    * a안에 a 불가

## labelledby를 이용해서 이미지와 피그캡션을 연결할 수 있다.


## float 해제


## IR 기법 image replace 기법 
    * 백그라운드로 이미지를 깔고 텍스트를 숨김처리 하는 기법.
```
padding 트릭
가볍지만 데이터에 문제가 있으면 텍스트도 나오지않음.

height: 0;
padding-top:195px;  
overflow:hidden;
```
```
text-indent 트릭
width값 만큼 indent값을 준다.
+ 줄바꿈 금지되는 white-space nowrap을 준다.
+ overflow hidden
```

## 백그라운드 sprite 기법



## 웹카페 신규이벤트 마크업 순서
1. 신규이벤트
1. 썸네일
1. 이벤트 내용
1. 이전/다음


## 관련사이트 마크업 수넛
1. 관련사이트
1. 사이트 목록

## 강조를 할 떄는 `strong, em` 태그 사용 / 디자인용이면 `span`



## btn-event
    * 버튼에 직접  IR기법을 쓰면 브라우저마다 많이 차이가 난다.
    * 그래서 버튼 부모태그에 height값과 overflow를 준다.



# 2018-09-19 수요일 HTML 9일차

## 인기사이트 마크업-디자인
    * sprite이미지 9*55 
### counter-increment : li 첫번째에는 1이라는 숫자, 두번째에는 2라느 ㄴ숫자가 자동으로 카운팅 된다.
    - before에 `content: counter(number)`라고 주면 1 2 3 4,, 라고 입력된다
    - (number, upper-alpha) 라고 입력하면 ABCD.. lower-alpha : Z..

### margin auto : 남아있는 영역을 마진으로 처리한다.

## 인용문 태그 
    1. `<q>` 
    1. `<blockquote>`  : 블럭상태의 인용문
    1. `cite="url"` 인용문의 출처를 올릴수있음

## 주소를 의미하는 `<address>` 태그
    * 푸터 영역에만 사용하는 태그임.
## 주로 저작권 문구(카피라이트)는 `<small>`을 이용한다



## [key code](http://keycode.info/)




