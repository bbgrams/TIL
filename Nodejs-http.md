# 2018-10-29 

## FDS Node.js + HTTP

(https://fds11.github.io/fds-nodejs-http/)[https://fds11.github.io/fds-nodejs-http/]

### REST API 실습

1. authentication
    - 인증절차
    - 내가 누군지를 밝혀야 자료를 줄 것.

1. 인증절차를 위한 토큰 생성
    - 깃헙 내 프로필의 settings - Developer settings - Personal access tokens
    - decript에는 토큰을 위한 설명 적어주고
    - 아무것도 체크하지않고(아무권한도없는)
    - 토큰 생성


### Node.js

1. 터미널에서 `node`를 입력 후 자바스크립트 사용 가능

1. 브라우저에 내장되어있는 기능은 사용할 수 없다(alert, prompt)

1. 브라우저와는 오나전히 다른 구동환경을 갖고있다.

1. 모듈은 내장함수를 갖고있는 객체이다.

1. `code test.js ` : test.js라는 파일을 vscode에서 열기

1. `node test.js` : test.js의 코드를 실행한다.

1. runtime : 구동환경

1. (https://fds11.github.io/fds-nodejs-http/1-1-2-node.html)[https://fds11.github.io/fds-nodejs-http/1-1-2-node.html]
    - 크롬에 내장되어있는 자바스크립트 해석기인 'V8'이 노드js에서도 사용되고있다.
    - 


1. `package.json`은 npm에 의해 관리되는 파일이다.
    - 보통 git에는 node_modules의 파일들은 추가하지않고, package.json 파일만 올린 후 npm install을 해서 해당 모듈을 다시 설치하는 방식으로 한다.
    - 개발자 편의를 위해 자주 사용되는 명령을 등록하는 용도로 더 많이 사용됨
        - index.js에 자주 사용하는 명령어를 적고,
        - 패지키제이선 파일의 스크립트 부분에 
        - `"test": "echo \"Error: no test specified\" && exit 1",
    "start": "node index.js"` 라고 적어주고
        - npm start를 하게 되면 index.js가 실행된다
        - 만약 " start1" : "node index.js"라고 쓰면 터미널에서 npm run start1 이라고 작성해야함.

1. 요즈음에는 프론트엔드 라이브러리도 npm에 올려서 사용한다.


### HTTP 

#### HTTP

1. 통신규약
1.  HyperText Transfer Protocol
1. 모바일 - 서버 간 통신
1. 서버 - 서버 간 통신
1. 속도가 빨라야 할때 사용

#### HTTP Methods
1. 기억해야할 메소드 CRUD
1. Create - (새로운 자료를 등록하는)Post(만들때)
1. Read - (자료의본문을 요청하는)Get(읽을때)
1. Update - Put, Patch(수정할때)
1. Delete - Delete (삭제할때)
1. [HTTP 요청 메소드](https://developer.mozilla.org/ko/docs/Web/HTTP/Methods)

#### HTTPS

1. HTTP over S(secure)SL : 암호화 된 HTTP
1. 개인정보를 다루고 있는 사이트는 https를 사용해야 한다.


#### HTTP/2

1. 엄청엄청엄청 빠르다.
1. 개발자 도구에서 Header 이름의 앞글자가 대문자이면 1버전, 소문자이면 2버전

### 요청과 응답 (Request & Response)

1. 웹 브라우저의 경우, HTML 문서 형태의 응답이 오면 해당 문서를 분석한 후, 문서에 포함된 모든 자원에 대한 요청을 각각 추가로 보냄 (이미지, 동영상, 오디오, CSS, JS, 폰트, ...)

1. Request Methods
    - 요청에는 메소드가 있다.
    - GET : 뭔가를 입력받을 때
    - POST : 뭔가를 제출할 때
    - PUT : 뭔가를 교체할 때( 게시물을 수정할 때 )

### URL
1. scheme 스킴. 프로토콜. 통신규약
2, 3, 4 : 도메인주소. 컴퓨터 주소. 호스트이름
5. 포트. 여기까지는 서버 주소 
6~ : 어떤 자원에 접속할 것인가. 자원 주소.
6 : 경로
7 : 쿼리스트링, 쿼리파라미터. 정확히 어떤자원을 가져올것인지. 부가정보
8 : 

### Header

- 요청과 응답에 대한 추가정보를 표현하는 데 사용됨.
- 인증, 캐싱, 쿠키, 보안, 프록시 등 웹 표준에 정의된 많은 기능을 제어하는데 사용됨.
- `user-Agent`
- `location`
- 위 두가지는 중요. 외워둬야 함.


## Express

1. 서버코딩을 더 쉽게 만들어주는 기술

1. glitch
    - `node.js`를 웹브라우저에서 실행시킬 수 있는 사이트
    - server.js에서 NAME이라는 환경변수를 불러와 표시해주고 있습니다
        - 프로그램을 실행하기전에 변수를 만들어 실행할 수 있다. 여기서 변수는 자바스크립트의 변수가 아니고 운영체제상의 변수이다. (환경변수  = 운영체제의 변수)
    -



# 2018-10-30

## Express 이어서..

1. Express 앱의 기본 구조
    ```js
    // Express 인스턴스 생성
    const app = express()

    // 미들웨어 주입
    app.use(sessionMiddleware())
    app.use(authenticationMiddleware())

    // 라우트 핸들러 등록
    app.get('/', (request, response) => { // 요청이 들어왔을때 요청을 분석해서 
    response.send('Hello express!') // send 메소드를 이용해서 서버(익스프레스)에서 브라우저로 응답을 보낸다.
    })

    // 서버 구동
    app.listen(3000, () => { // 3000번 포트에서 서버 실행 후 아래 함수를 실행하라.
    console.log('Example app listening on port 3000!')
    })
    ```

1. Routing

1. 요청 구성요소
    - 메소드
    - 주소
    - 헤더
    - 바디(파일, 이미지, 게시하고자하는 게시물의 내용 등..)

1. 응답 구성요소
    - 상태코드 (200번대, 300번대.. 404에러같은)
    - 헤더
    - 바디

1. [실습](https://glitch.com/edit/#!/recondite-ease)



## Template Language
1. EJS
1. [실습](https://glitch.com/edit/#!/equal-top)

1. [실습2](https://glitch.com/edit/#!/plant-money)


1. slug : 특정 자료를 대표하는 짧은 문자열


## HTML form

1. [실습](https://codepen.io/Shim-SoYoung/pen/wYbzmK)
1. [실습2](https://glitch.com/edit/#!/voracious-brook)
1. UUID(Universally unique identifier)
1. 새로고침이란 : 이전에 보냈던 요청을 다시 보내는 것


# 2018-10-31

## Cookie

- 정보를 저장하는 방법 1. HTTP Cookie : **서버가 응답을 통해 웹 브라우저에 저장하는** 이름+값 형태의 정보

### 쿠키 전송 절차

1.  서버는 브라우저에 저장하고싶은 정보를 응답과 같이 실어 보낸다.
1. 쿠키를 한번 받으면 정보가 저장되는데 그 정보를 다음번 요청할때 같이 실어서 보낸다. 몇번을 요청하던지, 매번 같이 실어서 보낸다.

1. Set-cookie options : 서버가 브라우저한테 저장하는 쿠키 설정하는 옵션.?

### 쿠키의 한계점

1. 인증토큰을 보통 쿠키에 저장한다.
1. 로그인 로그아웃을 할땐 쿠키를 많이 사용한다.

## Ajax

1. Ajax로 요청을 보내라 = 자바스크립트로 요청을 보내라 
1. ajax 요청을 보낼 수 있는 방법은 굉장히 다양하다.

### Axios

1. ajax 요청을 보낼 수 있는 여러가지 방법 중 하나.
1. 라이브러리이다.
1. Promise를 쓸 수 있어야만 axios를 쓸 수 있음
1. 어느 개발자가 사용하려고 만든 기능이라 아주 사용하기 편함.

1. [서버 구동 실습](https://glitch.com/edit/#!/instinctive-singer)
    - get method가 promise를 반환한다
    - `?title=react` 쿼리스트링. => json에 내장된 검색 기능. title에 react가 들어간 객체를 반환하라

1. [쿠키를 통한 인증 예제](https://glitch.com/edit/#!/conscious-larch)
    - 로그인 하지 않은 상태에서 Get을 하면 401 응답이 온다.


## CORS

### 동일 출처 정책
- 패캠에서 => `const child = window.open('http://www.fastcampus.co.kr')` 한 후 child.foo = 'bar' 가 가능한데
- 구글에서 => `const child = window.open('http://www.fastcampus.co.kr') ` 를 하면 출처가 같지않기때문에 진행이 안된다.

### CORS
- [cross-origin 요청 예제](https://glitch.com/edit/#!/interesting-woolen)



## JWT

깃헙에서 쓰는 인증방식
로컬스토리지
토큰을 저장하고있다가 요청할때마다 ..

# 2018-11-02

## JWT 이어서...

- 쿠키 : 브라우저가 자동으로 
- 회사마다 다름. 쿠키를 쓸 수도 있고 토큰을 쓸 수도 있기 때문에 두가지 모두 알고있어야함.
- jwt : 토큰을 만들어 내는 여러가지 방법 중 한가지.
- 토큰을 포함시키는 방법이나, 토큰의 세부적인 속성은 회사마다 다를 수 있다.
- 토큰을 어떻게 포함시켜야하는지 서버개발자에게 물어봐야함.

- 쿠키와 토큰의 차이
    



# 2018-11-05
## Fetch API

- 폴리필(polyfill) : 최신 브라우저 기능과 똑같이 만들어진 라이브러리

- Axios : 여러가지 편의 기능을 갖고있다. (개인 개발자가 본인이 쓰려고 만든것이기 때문에 쓰기 편하기 만드는데에 초점이 맞춰져있다) / 패치랑만 연동해서 쓸 수 있는 최신 기술을 사용할 수 없다

- fetch : promise를 반환한다

## HTTP Cache

- 통신에서 많이 쓰인다.
- ETag 라는 헤더가 있고 응답에서 쓰인다
    - 검증방식을 쓸 때는 자원의 식별자라는것을 만든다. 브라우저는 해당 정보를 식별자와 함께 저장하고 해당 식별자가 있는 자료끼리
    - 전체 자원을 전송하지않고도 자원이 바뀌었는지 확인할수있다.
    - 여기서 식별자를 ETag라는 헤더값이 포함해 전송한다.
    - (아래의 해시 내용 참고)
    - 식별자는 해시값을 사용한다
    - ETag ---- If-None-Match (둘을 묶어서 외움)
    1. 서버에서 브라우저에 식별자를 붙인 자원을 보낸다. 브라우저는 그 자원과 식별자를 저장한다. 다시 브라우저가 서버에 캐시를 확인할 때 `If-None-Match:abc123(식별자)` 라고 요청한다. 
    1. 식별자가 같으면(자원이 같으면) : 304 Not Modified status가 날라오고 그 자원을 그대로 사용한다.
    1. 식별자가 다르면(자원이 다르면) : 200 OK status를 보내고 바뀐 자원과 식별자를 보낸다.  

    
- 해시(hash) : 아래와 같은 특징을 갖고 있는 연산
    1. 같은 입력을 주면 항상 같은 출력이 나온다.
    1. 입력이 조금이라도 달라지면 완전히 다른 출력이 나온다
    1. [해시 md5 generator](http://www.miraclesalad.com/webtools/md5.php)

- 캐시는 읽는 작업을 할 때에만 동작한다.(POST에서는 아주 특별한 경우에만 동작하고 거의 대부분 동작하지않는다.)

- ** ETag - IfNoneMatch ** 는 외워두자!

- CDN(Contents Delivery Network) : 한 서버에서 모든 국가가 자원을 요청하면 멀리있는 국가는 시간이 오래 걸리기 때문에, 국가 혹은 대륙에 서버를 두고 인근 지역에서는 해당 서버에서 자원을 요청한다.


## GraphQl

- github은 두가지 API를 사용한다
    1. v3 : REST API
    1. v4 : GraphQL API
    1. [GraphQL 실습 ](https://developer.github.com/v4/explorer/)
    1. 좌 : 요청바디, 우 : 응답바디
    ```js
    //좌 요청바디 GraphQL
    query { 
        viewer { 
            login
            avatarUrl(size: 200)
            repositories(first: 10){
            totalCount
                nodes {
                createdAt
                name
                pushedAt
                resourcePath
                }
            }
        }
    }
    ```
    ```json
    // 우 : 응답바디 json
    {
        "data": {
            "viewer": {
            "login": "bbgrams",
            "avatarUrl": "https://avatars0.githubusercontent.com/u/42929997?s=200&v=4",
            "repositories": {
                "totalCount": 18,
                "nodes": [
                {
                    "createdAt": "2018-09-04T03:05:50Z",
                    "name": "fds-introduction",
                    "pushedAt": "2018-09-04T01:59:26Z",
                    "resourcePath": "/bbgrams/fds-introduction"
                },
                {
                    "createdAt": "2018-09-04T05:05:01Z",
                    "name": "fds-git",
                    "pushedAt": "2018-10-04T05:24:53Z",
                    "resourcePath": "/bbgrams/fds-git"
                },
                {
                    "createdAt": "2018-09-04T05:23:11Z",
                    "name": "fds-git-",
                    "pushedAt": "2018-09-04T05:23:12Z",
                    "resourcePath": "/bbgrams/fds-git-"
                }
                ]
            }
            }
        }
        }
        ```
- 편리하당.
- 하지만 널리쓰이진 않는당.ㅠㅠ
- graphQL 공부할 때 : [아폴로 그래프큐엘](https://www.apollographql.com/)


# 2018-11-06
## todolist 만들기
- [https://github.com/bbgrams/fds-mid-todo](https://github.com/bbgrams/fds-mid-todo)

## 게시판 만들기

1. parcel에는 환경변수를 사용하는 방법이 내장되어있다.
1. 테스트용 서버와 운영용 서버가 달라야한다. => baseURL이 그때그때 달라져야한다.
    - 외부에서 설정을 주입할수 있어야 하고

###  JSON서버의 내장기능
1. [내장기능](https://github.com/typicode/json-server#routes)
1. 이 안의 내장 기능을 모두 이해해야 쇼핑몰을 구현할 수 있다.
1. Plural routes : 
1. Filter : 파라미터를 이용해서 필터링
    ```js
    GET /posts?title=json-server&author=typicode // title이 json-server이고 
    GET /posts?id=1&id=2 //  id가 1인 경우와 id가 2인 경우를 가져오겟다
    GET /comments?author.name=typicode // 객체 안의 객체가 있는 경우
    ```
    `https://fds-json-server-bbs.glitch.me/posts?userId=1`
    `https://fds-json-server-bbs.glitch.me/posts?id=1&id=2`

1. Paginate 페이지네이션
Use `_page` and optionally `_limit` to paginate returned data.
In the Link header you'll get first, prev, next and last links. 
    ```js
    GET /posts?_page=7  // 7번페이지 get
    GET /posts?_page=7&_limit=20  // 한 페이지에 20개의 게시글 출력(limit)
    10 items are returned by default
    ```
    `https://fds-json-server-bbs.glitch.me/posts?_page=1&_limit=2`


1. Sort 정렬
    Add `_sort` and `_order` (ascending order by default)
    ```
    GET /posts?_sort=views&_order=asc
    GET /posts/1/comments?_sort=votes&_order=asc
    ```
    For multiple fields, use the following format:
    ```
    GET /posts?_sort=user,views&_order=desc,asc : 유저기준으로 내림차순 조회수기즌으로 오름차순
    ```
    Ascending : asc : 오름차순 
    Descending : desc : 내림차순
    `https://fds-json-server-bbs.glitch.me/posts?_sort=id&_order=desc` : 최신글부터 보여주고싶을때'

    `https://fds-json-server-bbs.glitch.me/posts?_sort=id&_order=desc&_limit=2&_page=1`     

1. Slice : 아이디가 20번인 애부터 30번인애까지 가져오쟈 할수있음. 넘어감

1. Operators
    Add `_gte` or `_lte` for getting a range
    ```
    GET /posts?views_gte=10&views_lte=20 조회수가 10보다 크거나 같고 20보다 작거나 같은
    ```
    Add `_ne` to exclude a value
    ```
    GET /posts?id_ne=1 아이디가 1이 아닌 놈
    ```
    Add `_like` to filter (RegExp supported)
    ```
    GET /posts?title_like=server 어떤 문자열이 이 문자가 포함되어있는지
    https://fds-json-server-bbs.glitch.me/posts?title_like=React 타이틀 속성에 리엑트가 포함되어있는 것들 
    posts?title=server : server라는 제목!의 글
    ```
    greater than  or equal = gte 크거나 같은
    less than or equal = lte 작거나 같은


1. Full-text search 전체 검색
    ```
    GET /posts?q=internet
    https://fds-json-server-bbs.glitch.me/posts?q=prop
    ```
    어느 속성이든 해당 문자열이 포함되어있는 속성을 검색한다. 텍스트로 상품 검색하기
    제목, 내용 상관없이 검색


1. Relationships 자료간의 관계
    To include children resources, add `_embed`
    ```
    GET /posts?_embed=comments
    GET /posts/1?_embed=comments
    https://fds-json-server-bbs.glitch.me/posts?_embed=comments : 게시물과 댓글을 한번에 가져올 수 있다
    https://fds-json-server-bbs.glitch.me/posts/1?_embed=comments : 1번게시물의 댓글들이
    ```
    To include parent resource, add `_expand` : 부모 자원을 가져오고 싶을 때
    ```
    GET /comments?_expand=post
    GET /comments/1?_expand=post
    https://fds-json-server-bbs.glitch.me/posts/1?_expand=user : 게시물을 소유하고있는 사용자 이름까지 표시된다(작성자)
    ```
    To get or create nested resources (by default one level, add custom routes for more)
    ```
    GET  /posts/1/comments
    POST /posts/1/comments : 1번게시글의 자식이되는 커멘트를 만들것이다.(댓글생성)
    ```

### axios
```
axios.get('/posts/', {
    params :{

    }
})
```
### URLSearchParams

같은 이름의 쿼리스트링을 여러번 써야하는경우에는  이걸 쓰면된다.

## 게시판 만들기
- 캐쉬가 제대로 안지워질때는 rm -f .cache 등 해서 진행하자.

-[서버 글리치](https://glitch.com/edit/#!/quiet-gull)

- 댓글의 작성자를 알려면, 요청을 두 번 보내야 한다.
    ```js
    const p = new URLSearchParams()
    p.append('id',1)
    p.append('id',2)
    p.toString() //  "id=1&id=2"
    ```



## 쇼핑몰 구현

- 상품 이름
- 가격
- 상품세부페이지
- 장바구니
- 장바구니에 담은 상품들을 구매하면 구매목록으로

1. `_embed` : 자식 데이터 불러올 때 사용. "복수" 적어줘야 함
    ```js
    //options!! 복수
    /products?_embed=options
    ```
1. `_expand` : 부모 데이터 불러올 때 사용. "단수" 적어줘야 함
    ```js
    // options 아님!
    /cartItems?_expand=option
    ```
1. 카테고리 필터링을 할 때는 json-server의 필터링 기능을 이용하세요
1. `/products?id=1&id=2` : 이런 요청을 보낼땐 URLparams를 써야함.


```js
//해보는중
https://broad-chauffeur.glitch.me/products/11?_embed=options&title=ice
```

1. 여러 부분에 걸쳐 적용되어야 하는 기능 : 횡단 관심사(cross-cutting concerns)
    - 코드 중복