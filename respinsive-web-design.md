# 2018-09-20 목요일 반응형 디자인

## flexible 반응형
    * 고무줄처럼 화면과 레이아웃이 같이 늘어남.
    * 컨텐츠량이 많거나 디자인이 복잡할땐 적합하지 않음.
    * 컨텐츠량이 적고 심플할때 적합.

## adaptive 적응형
    * 뷰포트에 따라 고정된 레이아웃.

## 반응형 디자인 패턴 (참고)
1. off canvas
1. calumn layout
1. ...등등

## 데스크탑 먼저 작업 후 모바일 작업
1. 모바일 화면에서 스타일이 재정의되기 때문에 속도가 느려짐.

## 모바일 먼저 작업 후 데스크탑
1. 모바일을 먼저 정의 후 점점 늘려가는 방법
1. 속도가 빠름.

## 반응형 관련 아키텍쳐 

1. Target / context = result
    - 900 / 960 = 0.9375
    - 컨텐츠 가로크기 나누기 실제컨텐츠크기(가로크기-양쪽여백)

1. 부모요소의 크기가 바뀔때마다 자식요소의 이미지 크기가 바뀜
```
img{
    max-width:100%
    height:auto;
}
이미지가 부모보다 클때는 부모크기에 맞게 줄어들음
이미지가 부모보다 작을 때는 최대 이미지크기만큼만 커짐.
(해상도가 깨지지않음)
```


1. 성능/속도 및 대역폭

1. 고해상도 디스플레이
    1. retina display


1. 다양한 이미지 포맷 대응
    1. 벡터형식의 이미지인 SVG 문법 
    1. 구글에서 제안한 WebP
    1. 마이크로소프트의 JPEG-XR
    1. FlashPix 같은 형식

1. 이미지 이슈 해결 방안
```
<img src="small.jpg"
    srcset="large.jpg 1024w, medium.jpg 640w, small.jpg 320w"
    sizes="(min-width:36em) 33.3vw, 100vw"
    alt="A rad wolf">

srcset 각각의 해상도 상황에 따라 이미지를 다르게 호출한다.
```

1. `<picture>` element
```
<picture>
    <source media="(min-width:40em)"
     srcset="big.jpg 1x, big-hd.jpg 2x">
     <source~>
     <img src = "fallback.jpg" alt="">
</picture>
최소 크기가 40em이상일때는 big 쓰고 아닐때는 밑의 이미지 씀.
둘다 안될 때는 fallback이미지 사용
```

1. device-pixel-ratio 배경

1. 웹디자인 할때 96 dpi로 놓고 해야함. 72는 노노

## Grid Layout
1. 라인으로 조절한다. 라인1 라인2...라인6
1. 속성
    1. grid-column-start : 
    1. grid-column-end:span 2; 내가 시작한 지점에서 몇칸 합칠것인지.
    현재 위치를 시작으로 두개의 컬럼을 병합한다.

1. 위치를 설정할 때 마크업 순서대로 배치가 되기때문에 header가 한 컬럼을 다 먹기때문에 굳이 grid-row 값을 주지 않아도 된다.




# 2018-09-21 금요일. 반응형 실습

## 반응형 콘텐츠 이미지 기술

* 방법 1.rwd-img
* 방법 2.srcset-pixel-ratio :1배율일떄, 2배율일때,,보여지는 이미지 처리 
    * 마크업이 지저분해질 수 있어서 보통 retina.js? 같은 라이브러리를 사용한다.
* 방법 3.srcset-sizes : 좀 복잡함.....
    * 550w, 1024w, 1600w는 이미지의 크기. 똑같은 이미지를 크기별로 만들어서  뷰포트의 크기에 따라 출력되는 이미지가 달라진다.
    * 1배율일때는 명확하게 디바이스 크기를 인식하여 이미지 호출(뷰포트처럼 정확하게 550일때는 스몰, 551일떄는 미디움)
    * 2배율화면의 250의 뷰포트를 가지면 small 이미지를 가져온다 (두배니까)
    * 2배율 화면의 551을 줬을때는 두배라 1102이지만 미디엄이미지를 가져온다.  1024가 1600보다 더 가까워서.
    * 현재 뷰포트크기나 배율에 따라 가장 근접한 이미지를 요청하는 기법
* 방법 4. picture (html5에 새롭게 추가된 신규요소)
    * picture를 쓸때는 항상 img 태그를 선언해줘야함.
    * srcset은 방법3이랑 동일하게 작동한다.
    * 반응형을 위한 클래스를 줄때는 반드시 img 태그에 줘야한다.
    * 익스플로러에서는 작동이 안됨. - polyfill 사용 가능.


## 반응형 배경이미지 기술
* background-size: contain, cover



## iFrame
* 연산식 쓰고 블럭 잡아 shift+ctrl+m 하면 자동 연산된다.


## rwd-video  동영상
* 


## 미디어쿼리
* @media all 모든 디바이스는 and (min-resolution:x) 최소 해상도 x 이상일떄
* `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
    * width=device-width 디바이스 물리적 너비를 사용한다. 이 코드를 사용해야함!
    