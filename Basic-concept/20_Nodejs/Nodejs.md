## # Nodejs

### # Nodejs

Chrome V8 javascript 엔진으로 빌드된 javascript 런타임이다.

<br>

### # 클라이언트와 서버

- 클라이언트

  클라이언트란 `요청을 보내는 주체`로 브라우저일 수도 있고, 데스크톱 프로그램일 수도 있고, 모바일 앱일 수도 있고, 다른 서버에 요청을 보내는 서버일 수도 있다.

- 서버

  서버는 네트워크를 통해 클라이언트에 정보나 `서비스를 제공(응답)`하는 컴퓨터 또는 프로그램을 말한다. 또한 서버라고 해서 요청에 대한 응답만 하는 것은 아니다. 다른 서버에 요청을 보낼 수도 있다. 이때는 요청을 보낸 서버가 클라이언트 역할을 한다.

<br>

### # 자바스크립트 런타임

런타임은 특정 언어로 만든 프로그램들을 실행할 수 있는 환경을 뜻한다. 노드는 자바스크립트 프로그램을 컴퓨터에서 실행할 수 있으므로 자바스크립트 실행기라고 봐도 무방하다. 기존에는 자바스크립트 프로그램을 자바스크립트 런타임을 내장하고 있는 브라우저에서만 실행할 수 있었지만 구글의 V8 엔진이 출시되고 V8 엔진을 기반으로 노드가 만들어졌다. 노드는 V8 엔진과 더불어 libuv 라이브러리를 사용한다.

<br>

### # libuv

libuv 라이브러리는 노드의 특성인 이벤트 기반, 논 블로킹 I/O 모델을 구현하고 있다.

<br>

### # 이벤트 기반

이벤트 기반이란 이벤트가 발생할 때 미리 지정해둔 작업을 수행하는 방식을 의미한다. 이벤트로는 클릭이나 네트워크 요청 등이 있을 수 있다. 이벤트 기반 시스템에서는 특정 이벤트가 발생할 때 무엇을 할지 미리 등록해두어야한다. 이를 이벤트 리스너에 콜백 함수를 등록한다고 표현한다. 노드도 이벤트 기반 방식으로 동작한다. 이벤트가 발생하면 이벤트 리스너에 등록해둔 콜백 함수를 호출한다. 발생한 이벤트가 없거나 발생했던 이벤트를 다 처리하면, 노드는 다음 이벤트가 발생할 때까지 대기한다. 이벤트 기반 모델에서는 이벤트 루프라는 개념이 등장한다. 여러 이벤트가 동시에 발생했을 때 어떤 순서로 콜백 함수를 호출할지를 이벤트 루프가 판단한다. (노드도 V8 엔진 위에서 동작하기 때문에 콜스택과 메모리힙을 사용하는 것이다.)

<br>

### # 이벤트 루프, 테스크 큐, 백그라운드

- 이벤트 루프

  이벤트 발생 시 호출할 콜백 함수들을 관리하고, 호출된 콜백 함수의 실행 순서를 결정하는 역할을 담당한다. 노드가 종료될 때까지 이벤트 처리를 위한 작업을 반복하므로 루프(loop)라고 부른다.

- 백그라운드

  setTimeout 같은 타이머나 이벤트 리스너들이 대기하는 곳이다. 자바스크립트가 아닌 다른 언어로 작성된 프로그램이라고 봐도 된다. 여러 작업이 동시에 실행될 수 있다.

- 테스크 큐

  이벤트 발생 후 백그라운드에서 테스크 큐로 타이머나 이벤트 리스너의 콜백 함수를 보낸다. 정해진 순서대로 콜백들이 줄을 서 있으므로 콜백 큐라고도 부른다. 콜백들은 보통 완료된 순서대로 줄을 서 있지만 특정한 경우에는 순서가 바뀌기도 한다. 선입선출의 자료구조를 가진다.

<br>

### # 논블로킹 I/O

이벤트 루프를 잘 활용하면 오래 걸리는 작업을 효츌적으로 처리할 수 있다. 작업에는 두 가지 종류가 있는데, 동시에 실행될 수 있는 작업과 동시에 실행될 수 없는 작업이다. 기본적으로 자바스크립트 코드는 동시에 실행될 수 없다. 하지만 자바스크립트상에서 돌아가는 것이 아닌 I/O 작업 같은 것은 동시에 처리될 수 있다. I/O는 입력(input)/출력(Output)을 의미한다. 파일 시스템 접근(파일 읽기, 파일 쓰기, 폴더 만들기 등)이나 네트워크를 통한 요청 같은 작업이 I/O의 일종이다. 이러한 작업을 할 때 노드는 논 블로킹 방식으로 처리하는 방법을 제공한다. 논 블로킹이란 이전 작업이 완료될 때까지 대기하지 않고 다음 작업을 수행함을 뜻한다. 반대로 블로킹은 이전 작업이 끝나야만 다음 작업을 수행하는 것을 의미한다. 노드는 I/O 작업을 백그라운드로 넘겨 동시에 처리하곤 한다. 따라서 동시에 처리될 수 있는 작업들을 최대한 묶어서 백그라운드로 넘겨야 시간을 절약할 수 있다. 예를 들어 하나당 1초가 걸리는 작업 1,2,3,4,5 중 3,4,5가 동시에 처리 가능한데 3 -> 1 -> 4 -> 2 -> 5 와 같이 묶어서 처리하지 않으면 5초가 걸린다. 이 때 3,4,5를 묶어서 처리하여 1 -> 3,4,5 -> 2 와 같이 묶어서 처리하면 3초 정도로 시간이 단축되는 것이다. 이렇게 작업 순서에 따라 성능이 크게 달라진다. 동시에 처리될 수 있는 I/O 작업이라도 논 블로킹 방식으로 코딩하지 않으면 의미가 퇴색되는 것이다.

```js
// 블로킹 방식의 I/O 예시
function longRunningTask() {
  // 오래 걸리는 작업
  console.log("작업 끝");
}

console.log("시작");
longRunningTask();
console.log("다음 작업");
// 결과 : 시작 -> 작업 끝 -> 다음 작업
```

```js
// 논 블로킹 방식의 I/O 예시
function longRunningTask() {
  // 오래 걸리는 작업
  console.log("작업 끝");
}

console.log("시작");
setTimeout(longRunningTask, 0);
console.log("다음 작업");

// 결과 : 시작 -> 다음 작업 -> 작업 끝
```

위와 같이 setTimeout(콜백, 0)은 코드를 논 블로킹으로 만들기 위해 사용하는 기법 중 하나이다. 사실 노드에서는 setTimeout(콜백, 0) 대신 다른 방식을 주로 사용하기는 한다. (ex setImmediate) 다만 아무리 논 블로킹 방식으로 코드를 작성하더라도
I/O 작업없이 코드가 전부 내가 작성한 것이라면 전체 소요 시간이 짧아지지는 않는다. 단순히 실행 순서만 바뀌는 것이다. 그렇다고 이런 상황에 논 블로킹이 의미 없는 것은 아니다. 오래 걸리는 작업을 처리할 때 논 블로킹을 통해 순서를 바꿔줌으로써 간단한 작업들이 대기되는 상황을 막을 수 있다. 또한 논 블로킹과 동시가 같은 의미가 아니라는 것을 알아야한다. 동시성은 동시 처리 가능한 작업을 논 블로킹 처리해야 얻을 수 있다. -> 내가 이해한 내용으로는 위와 같은 javascript 코드는 콜스택에서 하나씩 처리되므로 동시성을 가지고 있지 않고, javascript 코드에 API 요청 코드가 포함되는 경우 동시에 처리가 가능하므로 동시성을 가진다고 볼 수 있을 것 같다.

<br>

### # 싱글 스레드

싱글 스레드란 스레드가 하나뿐인 것을 의미한다. 스레드를 이해하기 위해서는 프로세스부터 알아야한다. 프로세스와 스레드의 차이는 다음과 같다.

- 프로세스는 운영체제에서 할당하는 작업의 단위이다. 노드나 웹 브라우저 같은 프로그램은 개별적인 프로세스이다. 프로세스 간에는 메모리 등의 자원을 공유하지 않는다.
- 스레드는 프로세스 내에서 실행되는 흐름의 단위이다. 프로세스는 스레드를 여러 개 생성해 여러 작업을 동시에 처리할 수 있다. 스레드들은 부모 프로세스의 자원을 공유한다. 같은 주소의 메모리에 접근 가능하므로 데이터를 공유할 수 있다.
- 도식화를 해보면 운영체제 안에 프로세스, 프로세스 안에 스레드 혹은 스레드들

노드는 싱글 스레드라고 여겨지는데 엄밀히 말하면 싱글 스레드로 동작하지 않는다. 노드를 실행하면 먼저 프로세스가 하나 생성된다. 그리고 그 프로세스에서 스레드들을 생성하는데 이때 내부적으로 스레드를 여러 개 생성한다. 그 중에서 작업자가 직접 제어할 수 있는 스레드는 하나뿐이다. 그래서 흔히 노드가 싱글 스레드라고 여겨진다. 이처럼 하나의 스레드만 직접 조작할 수 있으므로 요청이 많이 들어오면 한 번에 하나씩 요청을 처리한다. 블로킹이 심하게 일어나는 작업을 처리하지만 않는다면 스레드 하나로도 충분하다. 블로킹이 발생할 것 같은 경우에는 논 블로킹 방법으로 대기 시간을 최대한 줄인다.

<br>

### # 스레드풀과 워커 스레드

노드가 싱글 스레드로 동작하지 않는 두 가지 경우가 있다. 하나는 스레드풀이고, 다른 하나는 워커 스레드이다. 스레드풀은 노드가 특정 동작을 수행할 때 스스로 멀티 스레드를 사용한다. 대표적인 예로 암호화, 파일 입출력, 압축 등이 있다. 워커 스레드는 노드 12 버전에서 안정화된 기능으로 이제 노드에서도 멀티 스레드를 사용할 수 있게 되었다. 사용자가 직접 다수의 스레드를 다룰 수 있다. CPU 작업(연산이 많은 작업)이 많은 경우 워커 스레드를 사용하면 된다.

<br>

### # 싱글스레드 블로킹/논블로킹, 멀티스레드 블로킹/논블로킹

언뜻 보면 여러 개의 일을 동시에 처리할 수 있으므로 멀티 스레드가 싱글 스레드보다 좋아 보인다. 하지만 꼭 그런 것은 아니다. 이해를 돕기 위해 예시를 하나 들어보자.

한 음식점에 점원이 한명 있다. 손님은 여러 명이다. 점원 한명이 주문을 받아 주방에 넘기고, 주방에서 요리가 나오면 손님에게 서빙한다. 그 후 다음 손님의 주문을 받는다. 이런 구조라면 다음 손님은 이전 손님의 요리가 나올 때까지 아무것도 못하고 기다려야한다. 이것이 바로 `싱글 스레드(점원), 블로킹 모델`이다. 매우 비효율적이다.

이번에는 점원이 한 손님의 주문을 받고, 주방에 주문 내역을 넘긴 뒤 다음 손님의 주문을 받는다. 요리가 끝나기까지 기다리는 대신, 주문이 들어왔다는 사실만 주방에 계속 알려주는 것이다. 주방에서 요리가 완료되면 완료된 순서대로 손님에게 서빙한다. 요리의 특성(블로킹인지 논블로킹인지)에 따라 완료되는 순서가 다를 수 있으므로, 주문이 들어온 순서와 서빙하는 순서는 일치하지 않을 수 있다. 이것이 `싱글 스레드, 논 블로킹 모델`이다. 바로 `노드가 채택하고 있는 방식`이다. 점원은 한명이지만 혼자서 많은 일을 처리할 수 있다. 하지만 그 점원 한명이 아파서 쓰러지거나 하면 큰 문제(에러 처리를 제대로 못해 하나뿐인 스레드가 죽어 서버 전체가 멈추는 등)가 생길 수 있다. 또한, 요리를 하는 데 시간이 오래 걸린다면(CPU를 많이 쓰는 작업) 주문이 많이 들어왔을 때 버거울 수 있다.

멀티 스레드 방식에서는 손님 한 명이 올 때 마다 점원도 한 명씩 붙어 주문을 받고 서빙한다. 언뜻 보면 싱글 스레드보다 좋은 방법인 것 같지만, 장단점이 있다. 일단 손님 한 명당 점원도 한 명이면 서빙 자체는 걱정이 없다. 점원 한 명에게 문제가 생겨도 다른 점원으로 대체하면 되기 때문이다. 하지만 손님의 수가 늘어날수록 점원의 수도 늘어난다. 손님 수가 줄어들었을 때 일을 하지 않고 노는 점원이 있다는 것도 문제가 된다. 점원을 새로 고용하거나 기존 점원을 해고하는 데는 비용이 발생한다.

그렇다면 점원 여러 명(멀티 스레드)이 모두 논 블로킹 방식으로 주문을 받으면 더 좋지 않을까 하는 의문이 들 수 있다. 실제로 그렇다. 다만 멀티 스레드 방식으로 프로그래밍하는 것은 상당히 어려우므로 멀티 프로세싱 방식을 대신 사용한다. I/O 요청에는 멀티 프로세싱이 더 효율적이기도 하다. I/O 작업을 처리할 때는 멀티 스레딩보다 멀티 프로세싱이 효율적이므로 노드는 멀티 프로세싱을 많이 한다.

| 멀티 스레딩                                  | 멀티 프로세싱            |
| -------------------------------------------- | ------------------------ |
| 하나의 프로세스 안에서 여러 개의 스레드 사용 | 여러 개의 프로세스 사용  |
| CPU 작업이 많을 때 사용                      | I/O 요청이 많을 때 사용  |
| 프로그래밍이 어려움                          | 프로그래밍이 비교적 쉬움 |

<br>

### # 서버로서의 노드

노드는 기본적으로 싱글 스레드, 논 블로킹 모델을 사용하므로(자바스크립트 언어의 특성이기도 하다), 노드 서버 또한 동일한 모델일 수 밖에 없다. 따라서 노드 서버의 장단점은 싱글 스레드, 논 블로킹 모델의 장단점과 크게 다르지 않다. 서버에는 기본적으로 I/O 요청이 많이 발생하므로, I/O 처리를 잘하는 노드를 서버로 사용하면 좋다. 노드는 (논 블로킹 방식으로 코드를 작성했다는 가정 하에) libuv 라이브러리를 사용하여 I/O 작업을 논 블로킹 방식으로 처리한다. 따라서 스레드 하나가 많은 수의 I/O를 혼자서도 감당할 수 있다. 하지만 노드는 CPU 부하가 큰 작업에는 적합하지 않다. 이와 같은 특성을 고려했을 때 개수는 많지만 크기는 작은 데이터를 실시간으로 주고받는 데 적합하다. 네트워크나 데이터베이스, 디스크 작업 같은 I/O에 특화되어 있기 때문이다. 실시간 채팅 애플리케이션이나 주식 차트, JSON 데이터를 제공하는 API 서버가 노드를 많이 사용한다. 워커 스레드 기능을 통해 멀티 스레드 작업을 할 수 있지만 프로그래밍이 어렵다. 특히 스레드가 작업을 나눠서 처리할 수 있게 직접 나누어주는 것이 어렵다. 또한 멀티 스레드 프로그래밍을 하더라도 C, C++, Rust, Go와 같은 언어에 비해 속도가 느리다. 따라서 멀티 스레드 기능이 있다고 하더라도 이미지나 비디오 처리, 혹은 대규모 데이터 처리처럼 CPU를 많이 사용하는 작업을 위한 서버로는 권장하지 않는다.

노드에는 웹 서버가 내장되어 있다. 노드 외의 서버를 개발하다 보면 아파치, nginx, IIS처럼 별도의 웹 서버를 설치해야 하는 경우가 많다. 심지어 톰캣 같은 웹 애플리케이션 서버를 추가로 설치하는 경우도 있다. 하지만 노드는 내장된 웹 서버를 사용하면 되므로 편리하다. 하지만 나중에 서버 규모가 커지면 결국 nginx 등의 웹 서버를 노드 서버와 연결해야한다.

<br>

### # 노드의 장단점

- 장점

  1. 멀티 스레드 방식에 비해 적은 컴퓨터 자원 사용
  2. I/O 작업이 많은 서버로 적합
  3. 멀티 스레드 방식보다 쉬움
  4. 웹 서버가 내장되어 있음
  5. 자바스크립트를 사용함
  6. JSON 형식과 쉽게 호환됨

- 단점

  1. 기본적으로 싱글 스레드라서 CPU 코어를 하나만 사용
  2. CPU 작업이 많은 서버로는 부적합
  3. 하나뿐인 스레드가 멈추지 않도록 관리가 필요함
  4. 서버 규모가 커졌을 때 서버를 관리하기 어려움
  5. 어중간한 성능

<br>

### # 서버 외의 노드

처음에는 노드를 대부분 서버로 사용했지만, 노드는 자바스크립트 런타임이므로 용도가 서버에만 한정되지 않는다. 사용 범위가 저점 늘어나서 웹, 모바일, 데스크톱 애플리케이션 개발에도 사용된다. 노드 기반으로 돌아가는 대표적인 웹 프레임워크로는 앵귤러, 리액트, 뷰 등이 있다. 모바일 개발 도구로는 리액트 네이티브, 데스크톱 개발 도구로는 일렉트론 등이 대표적이다.

<br>

### # REPL 사용하기

자바스크립트는 스크립트 언어이므로 미리 컴파일을 하지 않아도 즉석에서 코드를 실행할 수 있다. 브라우저 콘솔 탭처럼 노드도 비슷한 콘솔을 제공하는데 입력한 코드를 읽고(Read), 해석하고(Eval), 결과물을 반환하고(Print), 종료할 때까지 반복한다(Loop)고 해서 RERL라고 부른다. 사용 방법은 다음과 같다. 터미널을 열고 node를 입력한다. 프롬프트가 `>`모양으로 바뀌었다면 자바스크립트 코드를 입력할 수 있다. `Ctrl + C`를 두번 누르거나 `.exit` 입력으로 종료할 수 있다.

<br>

### # JS 파일 실행하기

vs code에서 js 파일을 만든 뒤 해당 파일을 실행해보자. vs code에서 터미널을 열고 `node [자바스크립트 파일 경로]`(확장자 생략해도 됨)를 입력하거나, 해당 경로에서 `node [자바스크립트 파일명]`을 입력하면 실행할 수 있다. (ex `node /Users/yujaemin/Documents/13_nodejs/js/helloworld`, `node helloworld`)

<br>

### # 모듈로 만들기

모듈이란 특정한 기능을 하는 함수나 변수들의 집합이다. 예를 들면 수학에 관련된 코드들만 모아서 모듈을 하나 만들 수 있다. 모듈은 자체로도 하나의 프로그램이면서 다른 프로그램의 부품으로도 사용할 수 있다. 모듈로 만들어두면 여러 프로그램에 해당 모듈을 재사용할 수 있다. 자바스크립트 코드에서 코드를 재사용하기 위해 함수로 만드는 것과 비슷하다. 보통 파일 하나가 모듈 하나가 된다. 파일별로 코드를 모듈화할 수 있어 관리가 편하다. 노드는 CommonJS 모듈 시스템을 사용한다. 자바스크립트의 표준 모듈 시스템인 ES Modules을 사용하기 위해서는 mjs 확장자를 사용해야한다. mjs 확장자를 사용하지 않고 ES Modules을 사용하기 위해서는 package.json에 type: "module" 속성을 넣으면 된다.

<br>

### # global

브라우저의 window와 같은 전역 객체이다. 전역 객체이므로 모든 파일에 접근할 수 있다. 또한 window.open 메서드를 그냥 open으로 호출할 수있는 것처럼 global도 생략할 수 있다. 모듈 시스템인 require 함수도 global.require이 생략된 것이다. global 객체 내부에는 매우 많은 속성이 들어있다.

<br>

### # console

- console.time(레이블)

  console.timeEnd(레이블)과 대응되어 같은 레이블을 가진 time과 timeEnd 사이의 시간을 측정한다.

- console.log(내용)

  평범한 로그를 콘솔에 표시한다. console.log(내용, 내용, ...)처럼 여러 내용을 동시에 표시할 수 있다.

- console.error(에러 내용)

  에러를 콘솔에 표시한다.

- console.table(배열)

  배열의 요소로 객체 리터럴을 넣으면 객체의 속성들이 테이블 형식으로 표현된다.

- console.dir(객체, 옵션)

  객체를 콘솔에 표시할 때 사용한다. 첫 번째 인수로 표시할 객체를 넣고, 두 번째 인수로 옵션을 넣는다. 옵션의 colors를 true로 하면 콘솔에 색이 추가되어 보기가 한결 편해진다. depth는 객체 안의 객체를 몇 단계까지 보여줄지를 결정한다. 기본 값은 2이다.

- console.trace(레이블)

  에러가 어디서 발생했는지 추적할 수 있게 한다. 일반적으로 에러 발생 시 에러 위치를 알려주므로 자주 사용하지는 않지만, 위치가 나오지 않는다면 사용할만하다.

<br>

### # 타이머

타이머 기능을 제공하는 함수인 setTimeout, setnterval, setmmediate는 노드에서 window 대신 global 객체 안에 들어있다.

- setTimeout(콜백, 밀리초)

  주어진 밀리초(1000분의 1초) 이후에 콜백 함수를 실행한다.

- setInterval(콜백, 밀리초)

  주어진 밀리초마다 콜백 함수를 반복 실행한다.

- setImmediate(콜백)

  콜백 함수를 즉시 실행한다.

이 타이머 함수들은 모두 아이디를 반환한다. 아이디를 사용하여 타이머를 취소할 수 있다.

- clearTimeout(아이디)

  setTimeout을 취소한다.

- clearInterval(아이디)

  setInterval을 취소한다.

- clearImmediate(아이디)

  setImmediate를 취소한다.

<br>

### # setmmediate(콜백) vs setTimeout(콜백, 0)

setImmediate(콜백)과 setTimeout(콜백, 0)에 담긴 콜백 함수는 이벤트 루프를 거친 뒤 즉시 실행된다. 다만 특수한 경우에 setmmediate는 setTimeout(콜백, 0)보다 먼저 실행된다. 파일 시스템 접근, 네트워킹 같은 I/O 작업의 콜백 함수 안에서 타이머를 호출하는 경우이다. 하지만 setImmediate가 항상 setTimeout(콜백, 0)보다 먼저 호출되지 않기 때문에 헷갈리지 않도록 setTimeout(콜백, 0)은 사용하지 않는 것이 좋다.

<br>

### # `__filename`, `__dirname`

노드에서는 파일 사이에 모듈 관계가 있는 경우가 많으므로 때로는 현재 파일의 경로나 파일명을 알아야한다. 노드는 `__filename`, `__dirname` 이라는 키워드로 경로에 대한 정보를 제공한다.

<br>

### # module, exports, require

- module.exports

  모듈을 만들 때 사용한다. 초기에는 빈 객체({})를 참조하지만 객체, 함수 등 덮어씌울 수 있다. 즉 변수에 값을 할당하여 해당 변수가 모듈이 되는 것으로 봐도 무방하다.

- exports

  모듈을 만들 때 사용한다. module.exports는 한 번에 대입하는데 exports는 각각 넣을 수 있다. 이런 동작이 가능한 이유는 module.exports와 exports는 같은 객체를 참조하기 때문이다. export -> module.exports -> 빈 객체 혹은 할당한 객체, 함수 등을 참조한다. 주의할 점은 exports 객체 사용 시 module.exports와의 참조 관계가 깨지지 않도록 주의해야한다. module.exports에는 어떤 값이든 대입해도 되지만 exports에는 반드시 객체처럼 속성명과 속성값을 대입해야한다. 만약 다른 값을 대입하면 객체의 참조 관계가 끊겨 더 이상 모듈로 기능하지 않는다. 또한 exports를 사용할 때는 객체만 사용할 수 있으므로 함수를 대입한 경우에는 exports로 바꿀 수 없다. 이와 같이 참조 관계가 끊기는 위험 때문에 exports와 module.exports는 한 모듈에 동시에 사용하지 않는 것이 좋다.

  ```js
  exports.odd = "홀수입니다";
  exports.even = "짝수입니다";
  ```

- require

  모듈을 불러올 때 사용한다. require는 함수이고, 함수는 객체이므로 require는 객체로서 몇 가지 속성을 가지고 있다. 또한 require는 반드시 파일 최상단에 위치할 필요가 없고, module.exports도 최하단에 위치할 필요가 없다.

  - require.cache

    require.cache 객체에는 파일 이름이 속성명으로 들어 있는 것을 볼 수 있다. 속성 값으로 각 파일의 모듈 객체가 들어있다. 한 번 require한 파일은 require.cache에 저장되므로 다음 번에 require 할 때는 새로 불러오지 않고 require.cache에 있는 것이 재사용된다.

  - require.main

    require.main은 노드 실행 시 첫 모듈의 경로를 가리킨다. 이 스크립트가 직접 실행된 건지, 다른 데서 불러온 건지 판별할 수 있다.

<br>

### # 노드에서 this

노드에서 모듈 내 최상위 스코프에 존재하는 this는 module.exports(또는 export 객체)를 가리킨다. 또한 함수 선언문 내부의 this는 전역 객체인 global 객체를 가리킨다.

```js
console.log(this); // {}
console.log(this === module.exports); // true
console.log(this === exports); // true
function whatIsThis() {
  console.log(this === module.exports); // false
  console.log(this === global); // treu
}
```

<br>

### # 모듈의 순환 참조

만약 두 모듈 dep1과 dep2가 있고 이 둘이 서로를 require 한다면 어떻게 될까? 놀랍게도 dep1의 module.exports가 함수가 아닌 빈 객체로 표시된다. 이러한 현상을 순환 참조라고 부른다. 이렇게 순환 참조가 있을 경우에는 순환 참조되는 대상을 빈 객체로 만든다. 이때 에러가 발생하지 않고 빈 객체로 변경되므로 예기치 못한 동작이 발생할 수 있다. 따라서 순환 참조가 발생하지 않도록 구조를 잡아야한다.

```js
// dep1.js
const dep2 = require("./dep2");
console.log("require dep2", dep2);

module.exports = () => {
  console.log("dep2", dep2);
};
```

```js
// dep2.js
const dep1 = require("./dep1");
console.log("require dep1", dep1);

module.exports = () => {
  console.log("dep1", dep1);
};
```

```js
// dep-run.js
const dep1 = require("./dep1");
const dep2 = require("./dep2");

console.log(dep1); // {}
console.log(dep2); // Function (anonymous)]
```

<br>

### # process

process 객체는 현재 실행되고 있는 노드 프로세스에 대한 정보를 담고 있다. process.version, process.arch, process.platform, process.pid, process.uptime, process.execPath, process.cwd, process.cpuUsage, process.env, process.nextTick, process.exit 등 다양한 프로퍼티를 가지고 있다.

- process.env

  REPL에 process.env를 입력하면 매우 많은 정보가 출력된다. 자세히 보면 시스템 환경 변수임을 알 수 있다. 시스템 환경 변수는 노드에 직접 영향을 미치기도 한다. 대표적인 것으로 UV_THREADPOOL_SIZE와 NODE_OPTIONS가 있다. 왼쪽이 환경 변수 이름이고 오른쪽이 값이다. NODE_OPTIONS는 노드를 실행할 때의 옵션들을 입력받는 환경 변수이다. UV_THREADPOOL_SIZE와는 노드에서 기본적으로 사용하는 스레드풀의 스레드 개수를 조절할 수 있게 한다.

  ```bash
  NODE_OPTIONS=--max-old-space-size=8192
  UV_THREADPOOL_SIZE=8
  ```

  시스템 환경 변수 외에도 임의로 환경 변수를 저장할 수 있다. process.env는 서비스의 중요한 키를 저장하는 공간으로도 사용된다. 서버나 데이터베이스의 비밀번호와 각종 API 키를 코드에 직접 입력하는 것은 위험하다. 혹여 서비스가 해킹을 당해 코드가 유출되었을 때는 비밀번호가 코드에 남아 있어 추가 피해가 발생할 수 있다. 따라서 중요한 비밀번호는 다음과 같이 process.env의 속성으로 대체한다. process.env에 직접 환경 변수를 넣는 방법은 운영 체제마다 차이가 있다. 하지만 한번에 모든 운영체제에 동일하게 넣을 수 있는 방법이 있다. dotenv와 같은 Nodejs 애플리케이션에서 `.env` 파일에 정의된 환경변수를 process.env로 불러올 수 있게 해주는 라이브러리를 사용하면 된다.

  ```js
  const secretId = process.env.SECRET_ID;
  const secretCode = process.env.SECRET_CODE:
  ```

- process.nextTick

  이벤트 루프가 다른 콜백 함수들보다 nextTick의 콜백 함수를 우선으로 처리하도록 만든다. process.nextTick은 setImmediate나 setTimeout보다 먼저 실행된다. 또한 resolve된 Promise도 nextTick처럼 다른 콜백들보다 우선시된다. 그래서 process.Tick와 Promise를 마이크로태스크라고 따로 구분지어 부른다. 즉 마이크로태스크 큐에서 처리된다.

  하지만 주의할 점이 있다. process.nextTick으로 받은 콜백 함수나 resolve된 Promise는 다른 이벤트 루프에서 대기하는 콜백 함수보다 먼저 실행된다. 그래서 비동기 처리할 때 setImmediate보다 process.nextTick을 더 선호하는 개발자도 있다. 하지만 이런 마이크로태스크를 재귀 호출하게 되면 이벤트 루프는 다른 콜백 함수보다 마이크로태스크를 우선하여 처리하므로 콜백 함수들이 실행되지 않을 수도 있다.

  ```js
  // nextTick.js
  setImmediate(() => {
    console.log("immediate");
  });
  process.nextTick(() => {
    console.log("nextTick");
  });
  setTimeout(() => {
    console.log("timeout");
  }, 0);
  Promise.resolve().then(() => console.log("promise"));

  // node nextTick 결과
  // nextTick
  // promise
  // timeout
  // immediate
  ```

- process.exit

  실행 중인 노드 프로세스를 종료한다. 서버 환경에서 이 함수를 사용하면 서버가 멈추므로 특수한 경우를 제외하고는 서버에서 잘 사용하지 않는다. 하지만 서버 외의 독립적인 프로그램에서는 수동으로 노드를 멈추기 위해 사용한다. process.exit 메서드는 인수로 코드 번호를 줄 수 있다. 인수를 주지 않거나 0을 주면 정상 종료를 뜻하고, 1을 주면 비정상 종료를 뜻한다. 만약 에러가 발생해서 종료하는 경우에는 1을 넣으면 된다.

  ```js
  // exit.js
  let i = 1;

  setInterval(() => {
    if (i === 5) {
      console.log("종료 !");
      process.exit();
    }

    console.log(i);
    i += 1;
  }, 1000);
  // node exit 결과
  // 1
  // 2
  // 3
  // 4
  // 종료 !
  ```

<br>

### # 노드 내장 모듈

노드는 웹 브라우저에서 사용되는 자바스크립트보다 더 많은 기능을 제공한다. 운영체제 정보에도 접근할 수 있고, 클라이언트가 요청한 주소에 대한 정보도 가져올 수 있다. 노드에서 이러한 기능을 하는 모듈을 제공한다. 다만 노드 버전마다 차이가 있다.

<br>

### # os 모듈

웹 브라우저에 사용되는 자바스크립트는 운영체제의 정보를 가져올 수 없지만, 노드는 os 모듈에 정보가 담겨 있어 정보를 가져올 수 있다. process 객체와 겹치는 부분도 조금 있다.

```js
const os = require("os");
...
```

- os.arch() : process.arch와 동일하다.

- os.platform() : process.platform과 동일하다.

- os.type() : 운영체제의 종류를 보여준다.

- os.uptime() : 운영체제 부팅 이후 흐른 시간(초)을 보여준다. process.uptime()은 노드의 실행 시간이므로 차이가 있다.

- os.hostname() : 컴퓨터 이름을 보여준다.

- os.release() : 운영체제의 버전을 보여준다.

- os.homedir() : 홈 디렉터리 경로를 보여준다.

- os.tmpdir() : 임시 파일 저장 경로를 보여준다.

- os.cpus() : 컴퓨터의 코어 정보를 보여준다.

  - 코어 개수 확인하기 : os.cpus().length를 하면 코어의 개수가 숫자로 나온다. 하지만 노드에서는 싱글 스레드 프로그래밍을 하면 코어가 몇 개이든 상관없이 대부분의 경우 코어를 하나밖에 사용하지 않는다. 하지만 cluster 모듈을 사용하는 경우에는 코어 개수에 맞춰서 프로세스를 늘릴 수 있다. 이 때 cpus() 메서드를 사용할 수 있다.

- os.freemem() : 사용 가능한 메모리(RAM)을 보여준다.

- os.totalmem() : 전체 메모리 용량을 보여준다.

추가로 os.constants라는 객체가 있다. 그 안에는 각종 에러와 신호에 대한 정보가 담겨있다. 에러가 발생했을 때 EADDRINUSE나 ECONNRESET 같은 에러 코드를 함께 보여준다. 이러한 코드들이 os.constants 안에 들어 있다. 에러 코드가 너무 많아서 외울 수 없으므로 발생할 때마다 검색해보는 것이 좋다. os 모듈을 주로 컴퓨터 내부 자원에 빈번하게 접근하는 경우 사용된다. 즉 일반적인 웹 서비스를 제작할 때는 사용 빈도가 높지 않다. 하지만 운영체제별로 다른 서비스를 제공하고 싶을 때 os 모듈이 유용하다.

<br>

### # path 모듈

폴더와 파일의 경로를 쉽게 조작하도록 도와주는 모듈이다. path 모듈이 필요한 이유 중 하나는 운영체제별로 경로 구분자가 다르기 때문이다. 크게 윈도 타입과 POSIX 타입으로 구분된다. POSIX는 유닉스 기반의 운영체제들을 의미하며 맥과 리눅스가 속해 있다. 이 외에도 파일 경로에서 파일명이나 확장자만 따로 떼어주는 기능을 구현해두어 직접 구현하지 않고도 편리하게 사용할 수 있다.

```js
const path = require("path");
const string = __filename;
...
```

- path.sep : 경로의 구분자이다. 윈도는 `\`, POSIX는 `/`이다.

- path.delimiter : 환경 변수의 구분자이다. process.env.PATH를 입력하면 여러 개의 경로가 이 구분자로 구분되어 있다. 윈도는 세미콜론(`;`)이고, POSIX는 콜론(`:`)이다.

- path.dirname(경로) : 파일이 위치한 폴더 경로를 보여준다.

- path.extname(경로) : 파일의 확장자를 보여준다.

- path.basename(경로, 확장자) : 파일의 이름(확장자 포함)을 표시한다. 파일의 이름만 표시하고 싶다면 basename의 두 번째 인수로 파일의 확장자를 넣으면 된다.

- path.parse(경로) : 파일 경로를 root, dir, base, ext, name으로 분리한다.

- path.format(객체) : path.parse()한 객체를 파일 경로로 합친다.

- path.normalize(경로) : `/`나 `\`를 실수로 여러 번 사용했거나 혼용했을 때 정상적인 경로로 변환한다.

- path.isAbsolute(경로) : 파일의 경로가 절대경로인지 상대경로인지를 true나 false로 알린다.

- path.relative(기준경로, 비교경로) : 경로를 두 개 넣으면 첫 번째 경로에서 두 번째 경로로 가는 방법을 알린다.

- path.join(경로, ...) : 여러 인수를 넣으면 하나의 경로로 합친다. 상대경로인 ..(부모 디렉터리)과 .(현 위치)도 알아서 처리한다.

- path.resolve(경로, ...) : path.join()과 비슷하지만 차이가 있다. 동작 방식이 다르다. `\`를 만나면 path.resolve는 절대 경로로 인식해서 앞의 경로를 무시하고, path.join은 상대경로로 처리한다.

  ```js
  path.join("/a", "/b", "c"); // 결과 /a/b/c/
  path.resolve("/a", "/b", "c"); // 결과 /b/c
  ```

<br>

### # 노드의 상대경로와 절대경로

노드는 require.main 파일을 기준으로 상대 경로를 인식한다. 따라서 require.main과 다른 디렉터리의 파일이 상대 경로를 갖고 있다면 예상과 다르게 동작할 수 있다. 이 문제는 path 모듈을 통해 해결할 수 있다.

<br>

### # url 모듈

인터넷 주소를 쉽게 조작하도록 도와주는 모듈이다. url 처리에는 크게 두 가지 방식이 있다. 노드 버전 7에서 추가된 WHATWG(웹 표준을 정하는 단체의 이름) 방식의 url과 예전부터 노드에서 사용하던 방식의 url이 있다.

- WHATWG의 url

  url 모듈 안에 URL 생성자가 있다. 이 생성자에 주소를 넣어 객체로 만들면 주소가 부분별로 정리된다. 이 방식이 WHATWG의 url이다. WHATWG에만 있는 username, password, origin, searchParams 속성이 존재한다.

- 기존 방식의 url

  기존 노드 방식에는 두 메서드를 주로 사용한다. host 부분 없이 pathname만 오는 주소의 경우에는 해당 형식을 꼭 활용해야한다.

  - url.parse(주소)

    주소를 분해한다. WHATWG 방식과 비교하면 username과 password 대신 auth 속성이 있고, searchParams 대신 query가 있다.

  - url.format(주소)

    WHATWG 방식 url과 기존 노드의 url을 모두 사용할 수 있다. 분해되었던 url 객체를 다시 원래 상태로 조립한다.

- WHATWG의 url searchParams

  WHATWG 방식은 search 부분을 searchParams라는 특수한 객체로 반환하므로 유용하다. search 부분은 보통 주소를 통해 데이터를 전달할 때 사용된다. search는 물음표(`?`)로 시작하고 그 뒤에 `키=값` 형식으로 데이터를 전달한다. 여러 키가 있을 경우에는 `&`로 구분한다.

  - getAll(키)

    키에 해당하는 모든 값들을 가져온다. 예를 들어 url이 `https://www.gilbut.co.kr/?page=3&limit=10&category=nodejs&category=javascript`인 경우 nodejs와 javascript라는 두 가지 값이 들어있다.

  - get(키)

    키에 해당하는 첫 번째 값만 가져온다.

  - has(키)

    해당 키가 있는지 없는지를 검사하여 boolean을 반환한다.

  - keys()

    searchParams의 모든 키를 Iterator(반복기) 객체로 가져온다.

  - values()

    searchParams의 모든 값을 Iterator(반복기) 객체로 가져온다.

  - append(키, 값)

    해당 키를 추가한다. 같은 키의 값이 있다면 유지하고 하나 더 추가한다.

  - set(키, 값)

    append와 비슷하지만, 같은 키의 값들을 모두 지우고 새로 추가한다.

  - delete(키)

    해당 키를 제거한다.

  - toString

    조작한 searchParmas 객체를 다시 문자열로 만든다. 이 문자열을 search에 대입하면 주소 객체에 반영된다.

<br>

### # queryString 모듈

WHATWG 방식의 url 대신 기존 노드의 url을 사용할 때 search 부분을 사용하기 쉽게 객체로 만드는 모듈이다.

```js
const url = require("url");
const querysring = require("querystring");

const parsedUrl = url.parse(
  "https://www.gilbut.co.kr/?page=3&limit=10&category=nodejs&category=javascript"
);
const query = querysring.parse(parsedUrl.query);

console.log("querysring.parse(): ", query); // [Object: null prototype] { page: '3', limit: '10', category: [ 'nodejs', 'javascript' ] }
console.log("querysring.stringify(): ", querysring.stringify(query)); // page=3&limit=10&category=nodejs&category=javascript
```

- querystring.parse(쿼리)

  url의 query 부분을 자바스크립트 객체로 분해한다.

- querystring.stringify(객체)

  분해된 query 객체를 문자열로 다시 조립한다.

<br>

### # crypto 모듈

다양한 방식의 암호화를 도와주는 모듈이다. 고객의 비밀번호는 반드시 암호화해야 한다. 비밀번호를 암호화하지 않으면 비밀번호를 저장해둔 데이터베이스가 해킹당하는 순간, 고객들의 비밀번호도 고스란히 해커 손에 넘어가고 만다. 물론 데이터베이스가 해킹당하지 않도록 노력해야겠지만, 안전 장치를 이중으로 만들어놓는 것이 좋다.

- 단방향 암호화

  비밀번호는 보통 단방향 암호화 알고리즘을 사용해서 암호화한다. 단방향 암호화란 복호화할 수 없는 암호화 방식을 뜻한다. 복호화는 암호화된 문자열을 원래 문자열로 되돌려놓는 것을 의미한다. 즉, 단방향 암호화는 한 번 암호화하면 원래 문자열을 찾을 수 없다. 복화할 수 없으므로 암호화라고 표현하는 대신 해시 함수라고 부르기도 한다.

  복호화할 수 없는 암호화가 왜 필요한지 의문이 들 수 있다. 하지만 고객의 비밀번호는 복호화할 필요가 없다. 먼저 고객의 비밀번호를 암호화해서 데이터베이스에 저장한다. 그리고 로그인할 때마다 입력받은 비밀번호를 같은 암호화 알고리즘으로 암호화한 후, 데이터베이스의 비밀번호와 비교하면 된다. 원래 비밀번호는 어디에도 저장하지 않고 암호화된 문자열로만 비교하는 것이다.

  단방향 암호화 알고리즘은 주로 해시 기법을 사용한다. 해시 기법이란 어떠한 문자열을 고정된 길이의 다른 문자열로 바꿔버리는 방식이다. 예를 들어 abcdefgh라는 문자열을 qvew로 바꿔버리고 ijklm이라는 문자열을 zvsf로 바꿔버리는 것이다. 입력 문자열의 길이는 다르지만, 출력 문자열의 길이는 네 자리로 고정되어 있다.

  ```js
  const crypto = require("crypto");

  console.log(
    "base64 :",
    crypto.createHash("sha512").update("비밀번호").digest("base64")
  );
  console.log(
    "hex :",
    crypto.createHash("sha512").update("비밀번호").digest("hex")
  );
  console.log(
    "base64 :",
    crypto.createHash("sha512").update("다른 비밀번호").digest("base64")
  );

  // base64 : dvfV6nyLRRt3NxKSlTHOkkEGgqW2HRtfu19Ou/psUXvwlebbXCboxIPmDYOFRIpqav2eUTBFuHaZri5x+usy1g==
  // hex : 76f7d5ea7c8b451b773712929531ce92410682a5b61d1b5fbb5f4ebbfa6c517bf095e6db5c26e8c483e60d8385448a6a6afd9e513045b87699ae2e71faeb32d6
  // base64 : cx49cjC8ctKtMzwJGBY853itZeb6qxzXGvuUJkbWTGn5VXAFbAwXGEOxU2Qksoj+aM2GWPhc1O7mmkyohXMsQw==
  ```

  - 해시 함수 목록

    - createHash(알고리즘)

      사용할 해시 알고리즘을 넣는다. md5, sha1, sha256, sha512 등이 가능힞만, md5와 sha1은 이미 취약점이 발견되었다. 현재는 sha512 정도로 충분하지만, 나중에 sha512마저도 취약해지면 더 강화된 알고리즘으로 바꿔야한다.

    - update(문자열)

      변환할 문자열을 넣는다.

    - digest(인코딩)

      인코딩할 알고리즘을 넣는다. base64, hex, latin1이 주로 사용되는데, 그중 base64가 결과 문자열이 가장 짧아 애용된다. 결과물로 변환된 문자열을 반환한다.

  - 단방향 암호화의 단점

    1. 복호화 불가 : 원본 복원 불가, 실수 시 되돌리기 어려움
    2. 사용자 재설정 필요 : 비밀번호 분실 시 새로 설정해야 함
    3. 충돌 가능성 : 이론상 존재, 해시 함수 선택 중요
    4. 설정 실수 시 취약 : salt 미사용, SHA-256 등 빠른 해시 사용 시 위험
    5. 마이그레이션 어려움 : 기존 해시를 새로운 해시로 교체 어려움
    6. 사전 공격 가능 : 단순 입력은 레인보우 테이블로 뚫릴 수 있음

  - 단방향 암호화의 단점 보완 방법

    1. 무조건 salt 사용 (bcrypt/argon2는 자동 포함)
    2. 느리고 메모리 요구하는 해시 알고리즘 사용 (argon2id, bcrypt, scrypt)
    3. 사용자 로그인 시 점진적 마이그레이션
    4. 짧거나 흔한 비밀번호는 아예 금지 (1234, qwerty, password 등)

  - Rainbow Table vs Dictionary Attack

  | 항목        | 레인보우 테이블                                         | 사전(dictionary) 공격            |
  | ----------- | ------------------------------------------------------- | -------------------------------- |
  | 공격 방식   | 미리 해시 계산하여 `해시:평문` 목록 생성 후 저장 → 비교 | 평문만 저장 → 실시간 해싱 & 비교 |
  | 메모리 사용 | 크지만 빠름                                             | 적지만 느림                      |
  | 방어        | salt 필수                                               | salt + 느린 해시 필수            |

  - salt

    - 정의 : 해시 안전성을 높이기 위해 입력값에 추가하는 랜덤 문자열, 동일한 입력값이더라도 서로 다른 해시값이 나오도록 하는 기법

    - 목적 : 같은 비밀번호도 서로 다른 해시를 만들게 하여 공격 방어

    - 저장 : 해시값과 함께 저장 (별도로 또는 포함 형태로)

    - 자동 지원 : bcrypt, argon2 등은 내부적으로 자동 처리

    - 장점

      1. 무작위성 : 같은 입력값이라도 서로 다른 해시값 생성
      2. 레인보우 테이블 방지 : 미리 계산한 해시로는 뚫을 수 없음
      3. 사용자별 보호 : 여러 사용자들이 같은 비밀번호여도, 해시값이 다름

    ```js
    // salt 미사용시
    hash("1234") === hash("1234"); // 항상 true
    ```

    ```js
    // salt 사용시
    // 같은 비밀번호도 서로 다른 해시를 만들게 하여 공격 방어
    hash("1234") ➝ abcd1234...

    hash("1234" + "salt1") ➝ 78e9af...
    hash("1234" + "salt2") ➝ 94b2e0...
    ```

  - pbkdf2 예시

    ```js
    const crypto = require("crypto");

    crypto.randomBytes(64, (err, buf) => {
      const salt = buf.toString("base64");
      console.log("salt :", salt);

      crypto.pbkdf2("비밀번호", salt, 100000, 64, "sha512", (err, key) => {
        console.log("password :", key.toString("base64"));
      });
    });

    // salt : FiBZ7ANGju8o7z5YIX8kBt2Alk2xFUgpex9y0e5UMSmX3UC3HmVW6cyJukz+mFpHNeOXlaYyBHeg35lDfEd1xQ==
    // password : pOy+yp0YAJmtJ/mMbZ1m9YPQqrvoDUROSPqCoagncapg4lb3vBTByuLTb1b+ATpUuxuZ5G+5ALCE2lf5kEzJyw==
    ```

    먼저 randomBytes 메서드로 64바이트 길이의 문자열을 만든다. 이것이 salt가 된다. pdkdf2 메서드에는 순서대로 비밀번호, salt, 반복횟수, 출력 바이트, 해시 알고리즘을 인수로 넣는다. 위 예시는 sha512로 변환된 결괏값을 다시 sha512로 변환하는 과정을 10만 번 반복하는 것이다. 너무 많이 반복하는 것은 아닐지 걱정될 수도 있지만 1초 정도 밖에 걸리지 않는다. 싱글 스레드 프로그래밍을 할 때 1초 동안 블로킹이 되는 것은 아닌지 걱정할 수도 있지만 다행히 crypto.randomBytes와 crypto.pdkdf2 메서드는 내부적으로 스레드풀을 사용해 멀티 스레딩으로 동작한다. randomBytes이므로 매번 실행할 때마다 결과가 달라진다. 따라서 salt를 잘 보관하고 있어야 비밀번호도 찾을 수 있다. pdkdf2는 간단하지만 bycrypt나 scrypt보다 취약하므로 나중에 더 나은 보안이 필요하면 해당 방식을 사용해야한다.

- 양방향 암호화

  양방향 대칭형 암호화는 암호화된 문자열을 복화할 수 있으며 키(열쇠)라는 것이 사용된다. 대칭형 암호화에서 암호화를 복호화하려면 암호화할 때 사용한 키와 같은 키를 사용해야한다.

  ```js
  const crypto = require("crypto");

  const algorithm = "aes-256-cbc";
  const key = "abcdefghijklmnopqrstuvwxyz123456";
  const iv = "1234567890123456";

  const cipher = crypto.createCipheriv(algorithm, key, iv);
  let result = cipher.update("암호화할 문장", "utf8", "base64");
  result += cipher.final("base64");
  console.log("암호화", result);

  const decipher = crypto.createDecipheriv(algorithm, key, iv);
  let result2 = decipher.update(result, "base64", "utf8");
  result2 += decipher.final("utf8");
  console.log("복호화", result2);

  // 암호화 iiopeG2GsYlk6ccoBoFvEH2EBDMWv1kK9bNuDjYxiN0=
  // 복호화 암호화할 문장
  ```

  - crypto.createCipheriv(알고리즘, 키, iv)

    암호화 알고리즘과 키, iv를 넣는다. 암호화 알고리즘은 aes-256-cbc를 사용했으며 다른 알고리즘을 사용해도 된다. aes-256-cbc 알골지ㅡㅁ의 경우 32바이트여야 하고, iv는 16바이트여야 한다. iv는 암호화할 때 사용하는 초기화 벡터를 의미하지만 AES 암호화에 대해 따로 공부하는 것이 좋다. 사용 가능한 알고리즘 목록은 crypto.getChiphers()를 호출하면 볼 수 있다.

  - cipher.update(문자열, 인코딩, 출력 인코딩)

    암호화할 대상과 대상의 인코딩, 출력 결과물을 인코딩에 넣는다. 보통 문자열은 utf8 인코딩을, 암호는 base64를 많이 사용한다.

  - chipher.final(출력 인코딩)

    출력 결과물의 인코딩을 넣으면 암호화가 완료된다.

  - chipher.createDeciphervi(알고리즘, 키, iv)

    복호화할 때 사용한다. 암호화할 때 사용했던 알고리즘과 키, iv를 그대로 넣어야한다.

  - decipher.update(문자열, 인코딩, 출력 인코딩)

    암호화된 문장, 그 문장의 인코딩, 복호화할 인코딩을 넣는다. createChiphervi의 update()에서 utf8, base64 순으로 넣었다면 createDeciphervi의 update()에서는 base64, utf8 순으로 넣으면 된다/

  - decipher.final(출력 인코딩)

    복호화 결과물의 인코딩을 넣는다.

- 단방향 암호화 vs 양방향 암호화

  | 항목             | 양방향 암호화        | 단방향 해싱      |
  | ---------------- | -------------------- | ---------------- |
  | 복호화 가능 여부 | ✅ 가능              | ❌ 불가능        |
  | 사용 예          | 카드번호, 토큰, 통신 | 비밀번호 저장    |
  | 속도             | 느림 (보통)          | 빠름             |
  | 보안 방식        | 키 기반              | 충돌 회피/무결성 |

  양방향 암호화의 경우 키 유출 시 모든 비밀번호 복호화 가능하기 때문에 비밀번호 저장에는 절대 사용 금지이다. 해시(bcrypt, argon2id)를 사용해야 안전하다.

- 양방향 대칭키 암호화 vs 양방향 비대칭키 암호화

  - 대칭키 암호화

    암호화와 복호화에 같은 키 사용, 빠르고 효율적이나 키 유출 시 보안 무력화됨

  - 비대칭키 암호화

    암호화와 복호화에 서로 다른 키 (공개키/개인키) 사용, 공개키로 암호화하고 개인키로 복호화, HTTPS나 JWT 서명 등 데이터 전송에서 자주 사용, 속도는 느리지만 키 배포가 안전함

<br>

### # util 모듈

각종 편의 기능을 모아둔 모듈이다. 자주 사용되는 메서드는 아래와 같다.

- util.deprecate

  함수가 deprecated 처리되었음을 알린다. 첫 번째 인수로 넣은 함수를 사용했을 때 경고 메세지가 출력된다. 두 번째 인수로 경고 메세지 내용을 넣으면 된다. 함수가 조만간 사라지거나 변경될 때 알려줄 수 있어 유용하다.

- util.promisify

  콜백 패턴을 프로미스 패턴으로 바꾼다. 바꿀 함수를 인수로 제공하면 된다. 이렇게 바꿔두면 async/await 패턴까지 사용할 수 있어 좋다.

<br>

### # worker_threads 모듈

노드에서 멀티 스레드 방식으로 작업하는 것을 도와준다.

```js
// 예시1
const { Worker, isMainThread, parentPort } = require("worker_threads");

if (isMainThread) {
  // 부모일 때
  const worker = new Worker(__filename);
  worker.on("message", (message) => console.log("from worker", message)); // 워커로부터 메시지 받기
  worker.on("exit", () => console.log("worker exit")); // 워커가 종료되면 호출
  worker.postMessage("ping"); // 워커에게 메시지 보내기
} else {
  // 워커일 때
  parentPort.on("message", (value) => {
    console.log("from parent", value); // ping 출력
    parentPort.postMessage("pong"); // 부모에게 pong 응답
    parentPort.close(); // 워커 종료
  });
}

// 콘솔 실행 결과
// from parent ping
// from worker pong
// worker exit
```

isMainThread를 통해 현재 코드가 메인 스레드(기존에 동작하던 싱글 스레드를 메인 스레드 또는 부모 스레드라고 부른다)에서 실행되는지, 아니면 우리가 생성한 워커 스레드에서 실행되는지 구분된다. 메인 스레드에서 new Worker를 통해 현재 파일(`__filename`)을 워커 스레드에서 실행시키고 있다. 물론 현재 파일의 else 부분만 워커 스레드에서 실행된다. 부모에서는 워커 생성 후 worker.postMessage로 워커에 데이터를 보낼 수 있다. 워커는 parentPort.on('message') 이벤트 리스너로 부모로부터 메세지를 받고, parentPort.postMessage로 부모에게 메세지를 보낸다. 부모는 worker.on('message')로 메세지를 받는다. 참고로 메세지를 한 번만 받고 싶다면 once('message')를 사용하면 된다. 워커에서 on 메서드를 사용할 때는 직접 워커를 종료해야 한다는 점에 주의해야한다. parentPort.close()를 하면 부모와의 연결이 종료된다. 종료될 때는 worker.on('exit')이 실행된다.

이번에는 소수의 개수를 구하는 작업을 워커 스레드를 통해 비교해보자. 먼저 워커 스레드를 사용하지 않은 예시이다.

```js
const min = 2;
const max = 10000000;
const primes = [];

function generatePrimes(start, range) {
  let isPrime = true;
  const end = start + range;

  for (let i = start; i < end; i++) {
    for (let j = min; j < Math.sqrt(end); j++) {
      if (i !== j && i & (j === 0)) {
        isPrime = false;
        break;
      }
    }

    if (isPrime) {
      primes.push(i);
    }
    isPrime = true;
  }
}

console.time("prime");
generatePrimes(min, max);
console.timeEnd("prime");
console.log(primes.length);

// prime: 43.356s
```

2부터 1,000만까지의 숫자 중에 소수가 모두 몇 개 있는지를 알아내는 코드이다. 컴퓨터 성능에 따라 다르겠지만 상당한 시간이 소요된다. 이번에는 워커 스레드를 사용하여 여러 개의 스레드들이 문제를 나누어 풀도록 해본다. 멀티 스레딩은 상당히 어렵고 코드양도 많아진다.

```js
const {
  Worker,
  isMainThread,
  parentPort,
  workerData,
} = require("worker_threads");

const min = 2;
let primes = [];

function findPrimes(start, range) {
  let isPrime = true;
  const end = start + range;

  for (let i = start; i < end; i++) {
    for (let j = min; j < Math.sqrt(end); j++) {
      if (i !== j && i & (j === 0)) {
        isPrime = false;
        break;
      }
    }

    if (isPrime) {
      primes.push(i);
    }
    isPrime = true;
  }
}

if (isMainThread) {
  const max = 10000000;
  const threadCount = 8;
  const threads = new Set();
  const range = Math.ceil((max - min) / threadCount);
  let start = min;

  console.time("prime");
  for (let i = 0; i < threadCount - 1; i++) {
    const wStart = start;
    threads.add(
      new Worker(__filename, { workerData: { start: wStart, range } })
    );
    start += range;
  }
  threads.add(
    new Worker(__filename, {
      workerData: start,
      range: range + ((max - min + 1) % threadCount),
    })
  );
  for (let worker of threads) {
    worker.on("error", (err) => {
      throw err;
    });
    worker.on("exit", () => {
      threads.delete(worker);
      if (threads.size === 0) {
        console.timeEnd("prime");
        console.log(primes.length);
      }
    });
    worker.on("message", (msg) => {
      primes = primes.concat(msg);
    });
  }
} else {
  findPrimes(workerData.start, workerData.range);
  parentPort.postMessage(primes);
}
// prime: 9.750s
```

속도가 약 여섯 배 정도 빨라졌다. 워커 스레드를 여덟 개 사용했다고 해서 여덟 배 빨라지는 것은 아니다. 스레드를 생성하고 스레드 사이에서 통신하는데 상당한 비용이 발생하므로 이 점을 고려해서 멀티 스레딩을 해야 한다. 잘못하면 멀티 스레딩을 할 때 싱글 스레드보다 더 느려지는 현상도 발생할 수 있다.

<br>

### # child_process 모듈

노드에서 다른 프로그램을 실행하고 싶거나 명령어를 수행하고 싶을 때 사용하는 모듈이다. 이 모듈을 통해 다른 언어의 코드(예를 들면 파이썬)를 실행하고 결괏값을 받을 수 있다. 이름이 child_process(자식 프로세스)인 이유는 현재 노드 프로세스 외에 새로운 프로세스를 띄워서 명령을 수행하고 노드 프로세스에 결과를 알려주기 떄문이다.

```js
// 예시 1
const exec = require("child_process").exec;
const process = exec("ls");

process.stdout.on("data", function (data) {
  console.log(data.toString());
}); // 실행 결과

process.stderr.on("data", function (data) {
  console.error(data.toString());
}); // 실행 에러

// 콘솔 결과
// (현재 파일의 목록 표시)
```

이번에는 파이썬 프로그램을 실행해보자

```python
# 예시 2
# test.py
print('hello python')
```

```js
// 예시 2
const spawn = require("child_process").spawn;
const process = spawn("python3", ["test.py"]);

process.stdout.on("data", function (data) {
  console.log(data.toString());
});

process.stderr.on("data", function (data) {
  console.error(data.toString());
});

// 콘솔 출력 결과
// hello python
```

exec은 셸을 실행해서 명령어를 수행하고, spawn은 새로운 프로세스를 띄우면서 명령어를 실행한다. spawn에서도 세 번째 인수로 { shell : true }를 제공하면 exec처럼 셸을 실행해서 명령어를 수행한다. 셸을 실행하는지 마는지에 따라 수행할 수 있는 명령어에 차이가 있다.

<br>

### # 기타 모듈들

- assert

  값을 비교하여 프로그램이 제대로 동작하는지 테스트하는 데 사용한다/

- dns

  도메인 이름에 대한 IP 주소를 얻어내는 데 사용한다.

- net

  HTTP보다 로우 레벨인 TCP나 IPC 통신을 할 때 사용한다.

- string_decoder

  버퍼 데이터를 문자열로 바꾸는데 사용한다.

- tls

  TLS와 SSL에 관련된 작업을 할 때 사용한다.

- tty

  터미널과 관련된 작업을 할 때 사용한다.

- dgram

  UDP와 관련딘 작업을 할 때 사용한다.

- v8

  V8 엔진에 직접 접근할 때 사용한다.

- vm

  가상 머신에 직접 접근할 때 사용한다.

<br>

### # fs 모듈

fs 모듈은 파일 시스템에 접근하는 모듈이다. 즉, 파일을 생성하거나 삭제하고, 읽거나 쓸 수 있다. 폴더도 만들거나 지울 수 있다.

```txt
저를 읽어주세요.
```

```js
// readFile.js
const fs = require("fs");

fs.readFile("./readme.txt", (err, data) => {
  if (err) {
    throw err;
  }

  console.log(data);
  console.log(data.toString());
});

// 실행 결과
// <Buffer ec a0 80 eb a5 bc 20 ec 9d bd ec 96 b4 ec a3 bc ec 84 b8 ec 9a 94 2e>
// 저를 읽어주세요.
```

readFile의 결과물은 버퍼(Buffer)라는 형식으로 제공된다. 버퍼는 Node.js에서 이진(binary) 데이터를 직접 다룰 수 있도록 해주는 객체이다. 특히 파일, 네트워크, 스트림, 암호화 등에서 사용된다. Buffer는 파일의 내용을 바이너리(byte) 형태로 담고 있다. 즉 위 결과 중 첫 번째 결과는 UTF-8로 인코딩된 "저를 읽어주세요."라는 한글 문자열의 바이트 배열이다. 그렇기 때문에 toString()으로 디코딩해야 사람이 읽을 수 있는 문자열로 변환하면 두 번째 결과가 나온다.

fs는 기본적으로 콜백 형식의 모듈이므로 실무에서 사용하기가 불편하다. 따라서 fs 모듈을 프로미스 형식으로 바꿔주는 방법을 사용한다. fs 모듈에서 promise 속성을 불러오면 프로미스 기반의 fs 모듈을 사용할 수 있게 된다.

```js
// readFilePromise.js
const fs = require("fs").promises;

fs.readFile("./readme.txt")
  .then((data) => {
    console.log(data);
    console.log(data.toString());
  })
  .catch((err) => console.error(err));
```

결과는 위와 동일하다. 아래와 같이 파일을 만들 수도 있다. 아래 코드를 실행하면 writeme.txt 파일이 생성된다.

```js
// writeFile.js
const fs = require("fs").promises;

fs.writeFile("./writeme.txt", "글이 입력됩니다")
  .then(() => {
    return fs.readFile("./writeme.txt");
  })
  .then((data) => {
    console.log(data.toString());
  })
  .catch((err) => console.error(err));
```

<br>

### # fs 모듈 - 동기 메서드와 비동기 메서드

setTimeout 같은 타이머와 process.nextTick 외에도, 노드는 대부분의 메서드를 비동기 방식으로 처리한다. 하지만 몇몇 메서드는 동기 방식으로 사용할 수 있다. 특히 fs 모듈이 그러한 메서드를 많이 가지고 있다.

```js
// async.js
const fs = require("fs");

console.log("시작");
fs.readFile("./readme2.txt", (err, data) => {
  if (err) {
    throw err;
  }
  console.log("1번", data.toString());
});
fs.readFile("./readme2.txt", (err, data) => {
  if (err) {
    throw err;
  }
  console.log("2번", data.toString());
});
fs.readFile("./readme2.txt", (err, data) => {
  if (err) {
    throw err;
  }
  console.log("3번", data.toString());
});
console.log("끝");

// 콘솔 실행 결과
// 시작
// 끝
// 2번 저를 여러 번 읽어보세요.
// 3번 저를 여러 번 읽어보세요.
// 1번 저를 여러 번 읽어보세요.
```

같은 파일을 세 번 읽었다. 시작과 끝을 제외하고 결과는 다를 수 있다. 비동기 메서드들은 해당 파일을 읽으라고만 요청하고 다음 작업으로 넘어간다. 따라서 파일 읽기 요청만 세 번을 보내고 console.log('끝')을 찍는다. 나중에 읽기가 완료되면 백그라운드가 다시 메인 스레드에 알린다. 메인 스레드는 그제서야 등록된 콜백 함수를 실행한다. 이 방식은 상당히 좋다. 수백 개의 I/O 요청이 들어와도 메인 스레드는 백그라운드에 요청 처리를 위임한다. 그 후로도 얼마든지 요청을 더 받을 수 있다. 나중에 백그라운드가 각각의 요청 처리가 완료되었다고 알리면 그때 콜백 함수를 처리하면 된다. 백그라운드에서는 위 요청 세 개를 거의 동시에 실행한다.

- 동기와 비동기, 블로킹과 논 블로킹

  동기와 비동기, 블로킹과 논 블로킹이라는 네 개의 용어가 노드에서 혼용되고 있으며 의미도 서로 다르다.

  - 동기와 비동기 : 백그라운드 작업 완료 확인 여부

  - 블로킹과 논 블로킹 : 함수가 바로 return 되는지 여부

  노드에서 동기-블로킹 방식과 비동기-논 블로킹 방식이 대부분이다. 동기-논 블로킹이나 비동기-블로킹은 없다고 봐도 된다. 동기-블로킹 방식에서는 백그라운드 작업 완료 여부를 계속 확인하며 호출한 함수가 바로 return 되지 않고 백그라운드 작업이 끝나야 return 된다. 비동기-논 블로킹 방식에서는 호출한 함수가 바로 return 되어 다음 작업으로 넘어가며 백그라운드 작업 완료 여부를 신경 쓰지 않고 나중에 백그라운드가 알림을 줄 때 비로소 처리한다.

순서대로 출력하고 싶으면 다음 readFileSync 메서드를 사용할 수 있다.

```js
// sync.js
const fs = require("fs");

console.log("시작");
let data = fs.readFileSync("./readme2.txt");
console.log("1번", data.toString());
data = fs.readFileSync("./readme2.txt");
console.log("2번", data.toString());
data = fs.readFileSync("./readme2.txt");
console.log("3번", data.toString());
console.log("끝");

// 콘솔 출력 결과
// 시작
// 1번 저를 여러 번 읽어보세요.
// 2번 저를 여러 번 읽어보세요.
// 3번 저를 여러 번 읽어보세요.
// 끝
```

readFile 대신 readFileSync 메서드를 사용했다. 그런데 콜백 함수를 넣는 대신 직접 return 값을 받아온다. 그 값을 다음 줄부터 바로 사용할 수 있다. 코드는 훨씬 더 이해하기 쉽지만 치명적인 단점이 있다. readFileSync 메서드를 사용하면 요청이 수백 개 이상 들어올 때 성능에 문제가 생긴다. Sync 메서드를 사용할 때는 이전 작업이 완료되어야 다음 작업을 진행할 수 있다. 즉, 백그라운드가 작업하는 동안 메인 스레드는 아무것도 하지 못하고 대기하고 있어야 하는 것이다. 메인 스레드가 일을 하지 않고 노는 시간이 생기므로 비효율적이다. 백그라운드는 fs 작업을 동시에 처리할 수도 있는데, Sync 메서드를 사용하면 백그라운드 조차 동시에 처리할 수 없게 된다. 비동기 fs 메서드를 사용하면 백그라운드가 동시에 작업할 수도 있고, 메인 스레드는 다음 작업을 처리할 수 있다.

동기 메서드들은 이름 뒤에 Sync가 붙어 있어 구분하기 쉽다. writeFileSync도 있다. 하지만 동기 메서드를 사용해야 하는 경우는 극히 드물다. 프로그램을 처음 실행할 때 초기화 용도로만 사용하는 것을 권장한다. 대부분의 경우에는 비동기 메서드가 훨씬 더 효율적이다. 비동기 방식으로 하되 순서를 유지하고 싶다면 아래와 같이 할 수 있다.

```js
// asyncOrder.js
const fs = require("fs");

console.log("시작");
fs.readFile("./readme2.txt", (err, data) => {
  if (err) {
    throw err;
  }
  console.log("1번", data.toString());

  fs.readFile("./readme2.txt", (err, data) => {
    if (err) {
      throw err;
    }
    console.log("2번", data.toString());

    fs.readFile("./readme2.txt", (err, data) => {
      if (err) {
        throw err;
      }
      console.log("3번", data.toString());
      console.log("끝");
    });
  });
});

// 시작
// 1번 저를 여러 번 읽어보세요.
// 2번 저를 여러 번 읽어보세요.
// 3번 저를 여러 번 읽어보세요.
// 끝
```

이전 readFile의 콜백에 다음 readFile을 넣으면 된다. 이른바 콜백 지옥이 펼쳐지지만 적어도 순서는 보장한다. 콜백 지옥은 Promise나 async/await으로 어느 정도 해결할 수 있다. 결과는 위와 같다.

```js
const fs = require("fs").promises;

console.log("시작");
fs.readFile("./readme2.txt")
  .then((data) => {
    console.log("1번", data.toString());
    return fs.readFile("./readme2.txt");
  })
  .then((data) => {
    console.log("2번", data.toString());
    return fs.readFile("./readme2.txt");
  })
  .then((data) => {
    console.log("3번", data.toString());
    console.log("끝");
  })
  .catch((err) => console.error(err));
```

<br>

### # 버퍼와 스트림 이해하기
