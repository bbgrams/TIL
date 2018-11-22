# 2018-10-29

# 자바스크립트 심화2 - Iterable

1. iterable 객체를 생성하는 함수 => generator 함수
    - generator함수를 사용하면 무조건 객체를 반환한다.
    - 그 객체는 iterable protocol을 만족한다.

    ```js
    // generator 함수 선언하기
    function* gen1() {
      // ...
    }

    // 표현식으로 사용하기
    const gen2 = function* () {
      // ...
    }

    // 메소드 문법으로 사용하기
    const obj = {
      * gen3() {
        // ...
      }
    }
    ```
    - generator는 yield를 사용해서 일시정지를 할 수 있다.
    - (repl)[https://repl.it/@bbgrams/BrownPlasticCryptos]


# 2018-10-30

## 클래스

1. 객체에서는 콤마(,)가 있고, `class` 에서는 콤마(,)가 없다.
1. new
1. 정적메소드 : 생성자에 .찍고 사용하는 메소드(`Number.isNaN`,`Array.from`...)
1. 메소드를 다른 함수의 인수로 넘겨줘야 하는 경우 화살표 함수를 사용하는 것이 좋다.

# 2018-10-31

## 클래스

### 클래스 상속 

1. 클래스 기능의 꽃이당

1. super
    - 메소드 오버라이딩 (method overriding) : 부모클래스의 기능을 확장시키고 싶은 경우 일부러 이름 충돌을 일으켜서 ..~

1. 클래스필드 예제를 연습하려면 babel이 내장된 [repl](https://repl.it/languages/babel)에서 가능하다.

1. 부모클래스의..


## 큐

- 선입선출
- 스트리밍 기능

## 스택

- 후입선출
- ctrl + z 되돌리기 기능

## 비동기 프로그래밍

- 함수를 시간 간격을 두고 실행되게 하는 것 
- setTimeOut , clearTimeOut 
- setInterval, clearInterval 

1. 호출 스택 (Call Stack)
    - 실행흐름이 왔다갔다 하는데 이 흐름을 스택형태로 관리한다.
    - 모든 실행이 끝나면 호출 스택이 다 비워진다.
    - 호출 스택에 하나라도 들어있으면 브라우저가 먹통이 된다.
    - 자바스크립트 엔진이 관리하는 저장공간

1. 작업 큐(Task Queue)
    - 작업을 저장하는 공간. 무언가 처리가 일어나진 않는다.
1. call stack - API - task queue... 
1. 뭔가 처리가 일어나는 공간 : 콜스택, 브라우저
1. 다음 번 화면이 그려질 때(60fps, 16ms마다 화면이 그려짐)마다 작업을 하는 함수 : requestAnimationFrame

1. 비동기 프로그래밍
    - 브라우저에 부탁하고 넘어가는 방식

1. 콜백
    - 콜백이라고 해도 항상 비동기 인건 아니다.(동기식일수도있고 비동기식일수도 있음.)
    - 복잡한 비동기 작업을 할 수는 있지만 코드가 많이 많이 많이 복잡하다

1. promise★★★★★
    - 통
    - 나중에 값이 채워짐
    - 예제 11 - 2초뒤에 헬로라는 값이 채워지는 통을 만들었고,
    - 예제 12 -통에 값이 채워지는 순간 값을 반환해준다

# 2018-11-02

1. promise 이어서..

    - 작업큐를 사용함
    - 10번예제 무시
    - 11번예제, 12번예제
    ```js
    const p = new Promise((resolve, reject) => { // promise 생성 . 매개변수 둘 다 안에 함수가 들어옴
        setTimeout(() => { // 2초뒤에 실행되는 함수가 들어있는 코드 2초뒤에 헬로라는 resolve 값이 통 안에 채워짐.
            console.log('2초가 지났습니다.');
            resolve('hello');
        }, 2000);
    });

    p.then(msg => {
        console.log(msg); // hello
    });
    // 통이 만들어질 때에는 프라미스에 값이 안ㅊ채워져있다. then을 이용해서 콜백을 설정할 수 있는데 통이 채워지면(2초뒤에) resolve가 실행돼서 통에 헬로라는 값이 채워지면 msg가 콘솔에 출력된다.
    // 값이 채워졌을 때 콜백이 실행된다,,?..
    ```
    - `then`메소드 자체도 `promise`객체를 반환한다
        - 12번예제으 ㅣ결과값도 프라미스이다.
        - promise에 then 메소드를 쓸 수 있으니까 then다음에 then 다음에 then...계속 쓸 수 있다
        - 비동기 작업을 연속해서 작업할때 THEN을 이어붙여서 사용할수있다.
        - 연이어 비동기 작업을 하는 코드를 깔끔하게 작성할 수 있다.
    ```js
    p.then(msg => { //primise의 반환값 'hello'가 msg에 들어감
        return msg + ' world'; //'hello world'가 반환됨
    }).then(msg => { // then의 반환값 'hello world'가 msg에 들어감
        console.log(msg); // 'hello world'가 console에 출력됨.
    });
    ```
    - [promise객체를 반환하는 then,...](https://repl.it/@bbgrams/delay-promise-example)

    - 비동기작업을 연이어 할때 쉽게 작성할 수 있음.
    - 9번 예제와 17번 예제는 똑같은 작업을 하는 코드이다.(콜백과 promise)

### 비동기함수(Async Function)
1. async
    - 앞에 async를 붙이면 굉장히 다른 함수가 되고 사용할 수 있는 문법과 기능이 추가된다.
    - generater가 항상 iterable을 반환하는 것처럼, async 함수는 항상 promise를 반환한다.(return을 하든 안하든)
    ```js
    async function func1() {
  return 1;
    }

    async function func2() {
    return Promise.resolve(2); // 2가 채워진 통을 바로 반환
    }

    func1().then(console.log); // 1
    func2().then(console.log); // 2
    ```
1. await 
    - await 뒤에 promise를 쓸 수 있다.
    - await 뒤에 오는 promise가 결과값을 가질 때 까지 함수를 잠시 멈추고 , promise 통에 값이 채워지면 함수를 다시 실행하여 값을 반환한다.
    - 기다렸다가 함수가 실행된다.
    - await의 값을 변수에 저장할 수 있다.
    ```js
    const str = await delay(3000, 'hello') // 3초 뒤에 hello라는 값이 str에 저장된다.
    ```

- generator로도 비동기 처리를 할 수 있다.
- promise가 생기기 전에는 generator로 비동기 처리를 해주었다.
- async await는 브라우저가 일시정지를 해주지만 generator를 사용하면 yield를 이용해서 프로그래머가 직접 일시정지를 제어할 수 있기 때문에 일부러 generator를 사용하는 경우도 있다.


# axios README 읽기
- [axios](https://github.com/axios/axios#axiosconfig)
- 사용법을 읽을 때 배열이 들어가면 안되는 부분에 []대괄호가 있을 때, 이 부분은 생략 가능하다는 뜻임.
- aliases : 별명

# json server
- [jason server](https://github.com/axios/axios#axiosconfig)
- 실습용 서버 
- [실습 글리치](https://glitch.com/edit/#!/inexpensive-harbor)

# 할일 목록 웹사이트
- [할일 레플](https://repl.it/@bbgrams/axios-practice)
- 여러가지 처리 과정이 겹쳐버리면 문제가 생길 수 있다(광클했을때)
- 비동기코드를 둘러싸고있는 함수가 비동기함수여야한다.
-----
- 상태의 저장소가 멀리 떨어져있을때 ( 지금은 서버) 
- 믿을 수 있는 상태 저장소는 한개만 두는것이 좋다 (= Single Source of Truth)
- 상태를 한군데에만 저장하고 그 저장소를 믿는게 가장 좋다.
-----
- 실시간 웹 (realtime web)
- 트렐로, 슬랙
- 웹소켓을 이용해서 만들 수 있다.
- 요청을 보내지 않아도 정보를 바로 알 수 있다.

