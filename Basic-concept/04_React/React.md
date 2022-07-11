## # React

<br>

### # **SSR / CSR**

<br>

- SSR / CSR 이란?

  - SSR

    (1) 서버사이드 렌더링

    (2) MPA(Multi page application)에서 사용하는 렌더링 방식

    (3) 서버로부터 완전하게 만들어진 html파일을 받아와 페이지 전체를 렌더링

    (4) 쉽게 얘기해서 이미 다 그려진 DOM을 받게 되면 SSR 렌더링

  - CSR

    (1) 클라이언트 사이드 렌더링

    (2) SPA(Single page application)에서 사용하는 렌더링 방식

    (3) 서버에서 빈 html을 보내면 클라이언트에서 js를 통해 동적으로 태그들과 스타일을 생성하여 페이지를 구성하는 방식

    (4) 쉽게 얘기해서 뼈대만 받고 클라이언트(브라우저)에서 동적으로 DOM을 그리게 되면 CSR 렌더링

<br>

- SSR / CSR 장단점이 무엇인가?

  - SSR 장점

    (1) 빠른 초기 로딩 : 서버로 부터 화면 구성을 위한 HTML을 먼저 받아오기 때문에 초기 로딩이 빠름

    (2) SEO 유리 : 각각의 페이지가 존재하므로 SEO에 유리

  - SSR 단점

    (1) 서버 부하 높음 : 새로운 요청 시 서버가 모든 리소스를 준비해서 응답하므로 서버 부하 높고 로딩 속도 늦음

    (2) 떨어지는 사용자 경험(UX) : 새로운 요청 시 페이지가 새로고침 되므로 사용자 경험이 떨어짐

    (3) TTV와 TTI : HTML을 받아온 후 띄워놓고 JS를 받아오기 때문에 Time To View와 Time To Interact간에 시간 간격이 존재하여 이벤트 반응 없을 수 있음

  - CSR 장점

    (1) 서버 부하 낮음 : 새로운 요청 시 필요한 부분에 관련된 데이터만 응답하므로 서버부하가 낮고 로딩 속도 빠름

    (2) 자연스러운 사용자 경험(UX) : 새로운 요청 시 페이지가 새로고침 되지 않아 자연스러운 사용자 경험

  - CSR 단점

    (1) 느린 초기 로딩 : 초기에 모든 js 파일을 받아와야 하기 때문에 초기 로딩이 느림, 사용자에게 현재 불필요한 코드나 중복되는 코드 없이 적절한 사이즈의 코드가 적절한 타이밍에 동적으로 로드되도록 하는 code splitting 으로 해결 가능

    (2) SEO 불리 : 자바스크립트로 사용자와 상호 작용하기 전인 초기 html에는 데이터가 없어 SEO에 불리, react-helmet로 페이지별 메타 태그를 설정해주거나 pre-rendering을 통해 페이지별 정보를 제공하는 html파일을 생성할 수 있는 react-snap과 같은 라이브러리를 활용하여 SEO 최적화 가능

    (3) 화면 변하는 모습 노출 : 데이터가 없는 화면이 먼저 표시된 후, 비동기 요청을 통해 데이터를 서버로부터 받아온 후 화면을 재구성하게 된다. 해결 방법은 로딩 스피너 혹은 스켈레톤 UI를 통해 해결할 수 있다.

<br>

- SSR / CSR 동작 순서

  - SSR

    (1) 브라우저가 서버에 HTML, CSS, Javascript 파일 등 렌더링에 필요한 리소스 순서대로 요청

    (2) 서버에서 HTML, CSS 응답

    (3) 브라우저가 HTML/CSS파싱 -> 스타일 -> 레이아웃 -> 페인트 -> 컴포지트 단계를 거쳐 컨텐츠 렌더링

    (4) 컨텐츠 렌더링 후 Javascript 파일 요청, Javascript 파일이 로드되면 사용자와 DOM 요소 간 상호 작용 가능

  - CSR

    (1) 브라우저가 서버에 HTML 파일 요청

    (2) 서버에서 비어있는 HTML 파일 응답

    (3) HTML 파일 구성을 위한 Javascript 파일 요청

    (4) Javascript 파일 응답 받은 후 동적으로 HTML 파일 구성

    (5) 브라우저가 구성 된 HTML 파일을 로드 및 파싱하여 컨텐츠 렌더링

<br>

- React SSR 구현 방법 : https://velog.io/@kwonh/SSR-%EC%84%9C%EB%B2%84%EC%82%AC%EC%9D%B4%EB%93%9C%EB%A0%8C%EB%8D%94%EB%A7%812-SSR-%EC%A7%81%EC%A0%91%EA%B5%AC%ED%98%84-ReactDOMServer

<br>

- Next.js

  (1) SSR+CSR을 결합한 프레임워크

  (2) 첫 페이지에서는 SSR(서버 사이드 렌더링)방식으로 데이터가 채워진 html을 받아 SEO문제를 해결

  (3) 다음 페이지에서부터는 CSR(클라이언트 사이드 렌더링)방식으로 필요한 데이터만 서버에 요청

<br>

### # **React vs Vue vs Angular**

<br>

- Libraries, Frameworks 차이

  라이브러리는 흐름을 개발자가 직접 제어한다. 필요한 기능이 있을 때 라이브러리를 가져다 사용하는 것이다. 반대로 프레임워크는 프레임워크가 흐름을 가지고 있다. 프레임워크가 짜 놓은 틀에서 코드를 작성하게 된다.

<br>

- Libraries, Frameworks 사용하는 이유

  규모가 커지고 복잡한 애플리케이션을 개발하며 생산성을 향상시키고 많은 양의 데이터 관리와 코드 유지 보수를 더욱 편리하게 하기 위해 다양한 Frontend Framework,Library가 등장하고 사용하게 되었다.

<br>

- React(라이브러리), Vue(프레임워크), Angular(프레임워크) 중 React를 사용하는 이유

  처음 프레임워크, 라이브러리 사용하여 개발을 시작하게 되었을 때 React, Vue, Angular 중 React를 선택한 이유는 더 큰 개발 생태계를 가지고 있기 때문이었습니다. 현재도 npm 패키지 다운로드 수를 비교해보면 React 패키지 다운로드 수가 압도적입니다. 또한 React나 Vue 모두 오픈 소스이고 정기적으로 버전을 릴리즈하고 있지만 개인이 기업에 후원을 받아 관리되는 Vue보다 Facebook이 직접적으로 관리하는 React가 지속적으로 신뢰할 수 있는 라이브러리라고 생각했습니다.

<br>

### # **React란?**

<br>

- React의 특징

  (1) 가상 돔(Virtual DOM) : 가상 돔은 실제 DOM에 적용시키기 전 가상 DOM에 변화된 부분을 먼저 적용시킨 후 변화된 부분만 렌더링 되도록 하여 최소한의 연산을 통해 성능을 증가시킨다.

  (2) 단방향 데이터 바인딩 : 리액트는 데이터의 흐름은 단방향이다. 즉, 위에서 아래, 부모에서 자식, 한방향으로만 흐르며 거꾸로 부모의 데이터를 바꿔주기 위해서는 state를 이용해야 한다.

  (3) JSX 문법을 통한 선언형 프로그래밍 : JSX 문법을 사용한다. HTML을 작성하듯 사용하며 자바스크립트와 동시에 사용하고 HTML에 자바스크립트의 변수들을 바로 사용할 수 있는 일종의 템플릿 언어이다. JSX 문법을 사용하여 선언적으로 프로그래밍한다. 결과만 기술함으로써 코드 의도 파악이 쉽다. 예를 들어 렌더단에 js와 html 동시 사용하는 map이 있다.

  (4) 컴포넌트 기반 UI : 개별적인 뷰인 컴포넌트를 통해 UI를 구성한다.

<br>

- React의 장단점

  - 장점

    (1) 컴포넌트화 : 컴포넌트를 통해 재사용성을 증가시키고 유지보수 용이하게 함

    (2) 가상 돔 : 데이터 변경 -> 가상 DOM에 적용 -> 이전 가상 DOM과 비교 -> 변경된 부분 실제 DOM에 적용의 과정을 거쳐 DOM 연산 횟수를 줄이고 서버 부하를 줄임

    (3) 넓은 생태계 : Vue나 Angular에 비해 사용자가 압도적으로 많고 커뮤니티나 자료가 방대

  - 단점

    (1) 브라우저 호환성 : IE8 이하 버전은 지원하지 않음

    (2) 내장 기능 부족 : view 이외의 기능은 직접 구현하거나 써드파티 라이브러리(패키지,모듈)를 사용해야한다는 번거로움이 있음

<br>

### # **React Lifecycle Methods**

<br>

- 리액트 라이프사이클 순서

  생성(mount) -> 갱신(update) -> 제거(unmount)

<br>

- 각 메소드들을 언제 사용하는지?

  (1) componentDidMount : 컴포넌트가 생성된 직 후 호출

  (2) shouldComponentUpdate : props 또는 state가 새로운 값으로 갱신되어 렌더링이 발생하기 직전에 호출

  (3) componentDidUpdate : 리렌더링 완료 후 호출

  (4) componentWillUnmount : 컴포넌트가 화면에서 사라지기 직전에 호출

  (5) componentDidCatch : render 함수 에러 발생 시 호출

<br>

- 라이프사이클 중 써본 메소드가 뭐가 있는지?

  클래스형으로 작업하지 않기 때문에 라이프사이클 메소드는 사용해본 적이 없다. 대신 생명주기 메서드를 대체할 수 있는 useEffect hook을 자주 사용하였다. useEffect에 의존성 배열로 빈 대괄호를 사용하면 componentDidMount의 역할을 하고, 함수를 return하면 componentWillUnmount 역할을 한다. 또한 의존성 배열을 아예 사용하지 않거나, 의존성 배열에 값을 넣어 componentDidUpdate를 대체할 수 있다.

<br>

- react의 setState를 왜 사용하는지

  컴포넌트는 현재의 state와 setState를 얕은 비교해서 setState의 참조가 바뀌게 되면 업데이트 됬다고 감지하게 되어 render 함수를 호출하는데, state를 직접 setState의 참조가 바뀌지 않아 render 함수를 호출하지 않게 되어 상태 변경이 일어나도 리렌더링이 일어나지 않는다. 상태 변경을 추적하고 변경에 따라 구성 요소의 최신화를 유지하기 위해서는 setState를 사용해야 한다.

<br>

- componentDidMount 와 render 중 무엇이 먼저 실행되는지?

  componentDidMount 메서드보다 render 메서드가 먼저 실행되는 것으로 알고 있다.

<br>

### # **가상 돔(Virtual DOM)**

<br>

- 하나의 DOM 노드가 조작될 때마다 DOM 트리와 스타일 규칙들이 수정되므로 렌더 트리 생성, 레이아웃(리플로우), 페인트(리페인트) 단계를 다시 거친다. 이처럼 DOM객체의 크기나 위치가 변경되었을 때, 연관되는 DOM객체들의 위치와 크기를 재연산하여 배치하는 레이아웃 단계를 다시 거치는 것을 리플로우라고 하며, 리플로우가 일어나거나 DOM객체의 색상 혹은 글 내용 등이 바뀌었을 때 페인트 단계를 다시 거치는 것을 리페인트라고 한다. DOM 노드 하나를 조작할 때마다 리플로우나 리페인트 작업이 되면 브라우저의 성능 저하를 유발하게 된다. react에서 리플로우와 리페인트를 최소화하기 위해 등장한 것이 버츄얼 돔이다. 버츄얼 돔은 실제 DOM의 상태를 메모리에 저장해놓고 메모리 상에서 변경 전과 변경 후의 상태를 비교한 뒤 최소한의 내용만 실제 DOM에 반영 하는 프로그래밍 개념이다. 싱글 페이지 애플리케이션은 클라이언트 사이드 렌더링 방식을 채택하여 사용하는데 클라이언트 사이드 렌더링 방식에서는 잦은 DOM의 변화가 일어난다는 특징이 있다. 그런데 DOM에 변화가 일어날 때마다 리렌더링 과정을 반복하게 되면 많은 연산 비용이 발생하게 되므로 성능 이슈가 발생할 수가 있다. 하지만 버츄얼 돔은 실제 렌더링하는 것이 아닌 메모리 상에서 동작하기 때문에 훨씬 빠르고 여러 번에 상태 변화 시 버츄얼 돔에 우선 적용 후 배치처리를 통해 한번만 실제 돔에 반영시키므로 리렌더링도 한번만 발생시키므로 연산 비용이 적어 큰 성능 향상에 이득을 얻게 된다.

<br>

### # **Props / State**

<br>

- Props란?

  상위 컴포넌트가 하위 컴포넌트에 전달하는 데이터를 가진 객체이다. 단방향 데이터 흐름을 가지며 자식 입장에서는 직접 수정할 수 없다는 특징이 있다. 변수, state, 함수 등 모두 전달할 수 있다.

<br>

- State란?

  컴포넌트 내부에서 가지고 있는 컴포넌트의 상태값이다. 유동적인 데이터를 다루기 위한 객체이다.

<br>

- let으로 변수 선언해서 관리하면 될껄 왜 state로 관리하나?

  state는 일반 변수와 다르게 값이 변하게 되면 리렌더링이 일어난다. 값이 변함에 따라 관련 컴포넌트들이 업데이트되어야 하기 때문에 리렌더링이 발생하는 state를 사용하는 것이다.

<br>

- Props와 State의 차이

  (1) props는 자식 컴포넌트로 전달되고 state는 컴포넌트가 직접 관리한다.

  (2) props는 직접 변경할 수 없고 state는 직접 변경이 가능하다.

<br>

- 왜 state를 직접 변경하지 않고 setState를 이용하나요?

  만약 컴포넌트의 state를 직접 변경하면 react는 컴포넌트를 다시 렌더링해야 하는지 알 수 없다. setState 메소드를 사용하면 react는 state의 변화를 감지해 리렌더링을 발생시켜 컴포넌트를 업데이트 시킬 수 있다.

<br>

- 리액트에서 setState는 비동기 동작인가요, 동기 동작인가요?

  setState는 비동기로 동작한다. 비동기로 동작하는 이유는 일정 시간동안 변화하는 상태를 모아 한번에 렌더링하기 위해서이다. 리액트의 배치 업데이트(batch update)는 16ms(밀리세컨드)당 한번만 일어난다. 그러므로 상태 업데이트 후 바로 상태 값을 참조하여 다른 작업을 할 때 문제가 발생할 수 있다. 이런 경우 이전 상태를 바로 참조할 수 있는 prevState를 활용하여 상태를 업데이트 한 후 사용하는 방식으로 해결 할 수 있다. prevState는 setState안에 화살표 함수를 통해 파라미터로 이 전 state를 전달하는 방식으로 사용할 수 있다. (ex : `setState((prev) => prev + 1`)

<br>

- setState가 비동기 동작을 취했을 때 얻을 수 있는 이점은 무엇인가요?

  setState가 여러 번 호출 될 경우 호출 될 때마다 리렌더링이 발생하면 성능 저하가 발생할 수 있다. 그러므로 react는 batch update를 16ms마다 진행하여 만약 16ms 안에 100개의 state 변화가 일어난다면 변화 된 상태 값을 취합하여 한번에 업데이트 시키는 것이다. 결론은 setState의 비동기 동작으로 인해 성능 저하를 막을 수 있다는 것이다.

<br>

### # **react 리렌더링 조건**

<br>

(1) 부모 컴포넌트가 렌더링 될 때

(2) 자신의 state가 변경 될 때, 단 setState를 사용하여 변경해야한다. state를 직접 변경할 경우 state의 변경을 감지하지 못하기때문에 render 함수가 호출 되지 않는다.

(3) 자신이 전달받은 props가 변경될 때

<br>

### # **컴포넌트**

<br>

- 컴포넌트에 대해 설명해달라

  재사용이 가능한 UI 구성 단위이다. 컴포넌트는 재사용이 가능하고, 개별로 관리되기 때문에 유지 보수에 좋고 렌더단(render 함수 내)에서 페이지 구성을 파악하기 편하다.

<br>

- 컴포넌트를 나누는 기준

  (1) 페이지를 구성하는 요소 (nav, footer 등)

  (2) 재사용이 필요한 반복되는 요소인 경우

  (3) 한 컴포넌트 내에 코드 길이가 길어 가독성이 떨어지는 경우

<br>

### # **Hooks 란?**

<br>

- Hooks란?

  공식 문서에서는 Hook은 함수 컴포넌트에서 React state와 생명주기 기능을 연동할 수 있게 해주는 함수라고 한다. react를 클래스 없이 사용할 수 있게 해준다. 클래스형 컴포넌트의 단점을 보완하기 위해 만들어졌다. 최상위 레벨에서 호출해야하며 함수 컴포넌트 내에서 호출해야한다.

<br>

- Hooks가 만들어진 이유는?

  클래스형 컴포넌트에

  (1) extends와 super(props)를 매번 작성

  (2) 함수, props 등 사용 시 매번 this에 bind 후 사용

  (3) 고차 컴포넌트 지옥

  와 같은 문제로 인해 Hooks가 만들어지게 되었다.

<br>

- Hooks를 어떻게 사용했는지?

  useState, useEffect, useNavigate, useCallback, useMemo, useRef, useQuery, useInview, custom hook 등을 사용하였다.

<br>

- 클래스형 컴포넌트와 함수형 컴포넌트의 차이

  (1) 선언 방식 (클래스 class로 시작하고 컴포넌트로 상속, 함수 일반 함수 생성과 동일)

  (2) lifeCycle 관련 기능 사용 여부 (클래스 O, 함수 X)

  (3) 메모리 자원 사용량 (클래스 > 함수)

  (4) state, props 사용 방법 (클래스 this로 사용, 함수 this없이 사용)

<br>

### # **hook을 사용할 때의 가장 큰 장점은?**

<br>

- 로직의 재사용 가능, 관리가 쉽다

  Hook은 함수형 컴포넌트 이므로 함수 안에서 다른 함수를 호출하는 것으로 새로운 Hook을 만들어 볼 수 있기 때문이다. 따라서 리액트의 내장되어있는 Hook과 다른 사람들이 만든 여러 custom Hook을 레고처럼 조립해서 쉽게 custom Hook을 만들 수 있다.

<br>

- 로직을 한 곳으로 모을수 있어서 가독성이 좋다

  클래스형 컴포넌트의 라이프사이클 API는 서로 다른 로직이 하나의 메서드에 섞여 있어서 가독성이 좋지 않다. Hook은 같은 로직을 한 곳으로 모을 수 있다.

<br>

- Wrapper 컴포넌트양 감소

  고차 컴포넌트를 커스텀 훅으로 대체하면, Wrapper 컴포넌트를 사용하지 않아도 간단하게 구현할 수 있다.

<br>

- 정적 타입 언어로 타입을 정의하기 쉽다

  고차 컴포넌트의 타입 정의에 비해 정적 타입 언어로 타입을 정의 하기 쉬워졌다고 한다.

<br>

### # **Immutability**

<br>

- 리액트에서 객체가 {...spread} 사용하여 리턴해주는데, 그 이유가 무엇인가(불변성)

  불변성은 변하지 않는 상태나 값을 말한다. 리액트에서 값을 직접적으로 변경을 하지 않고, 기존의 값을 수정하지 않으면서 새로운 값을 만들어내는 것을 의미한다. 리액트는 얕은 비교를 통해 state의 업데이트를 감지한다. 얕은 비교는 실제 내부 값까지 비교하는 것이 아닌 참조하는 값에 메모리 주소를 비교하는 것이다. 이전 값과 현재 값에 얕은 비교를 수행하여 현재 값이 새로운 참조 값을 참조할 때 업데이트가 발생하게 되는 것이다. 하지만 state를 직접 변경하게 되면 이전 값과 현재 값에 참조 값이 바뀌지 않으므로 렌더링이 발생하지 않는다. 리액트에서 객체가 `setState([...state, newState])`와 같이 이전 값과 새로운 값을 spread 문법을 사용하여 리턴해주는 이유도 불변성을 지키기 위해서이다. 불변성을 지켜줌으로써 예상하지 못한 변화를 일으키지 않아 사이드 이펙트를 방지할 수 있고 효과적인 상태 업데이트를 할 수 있다.

<br>

### # **Redux란?**

<br>

- 리덕스를 사용해 봤는지.

  사용해보았는데 학습 목적으로만 사용해보고 실제 프로젝트에는 적용시켜보지 않았다. 프로젝트에서 전역 상태 관리가 필요할 때는 리코일을 사용하거나 리덕스 툴킷을 사용했었다.

<br>

- 리덕스의 디자인 패턴은 무엇이며, 그 패턴이 갖는 장점과 단점은 무엇인지?

  리덕스 디자인 패턴은 FLUX 패턴이다. MVC 패턴의 단점으로 FLUX 패턴이 생겨났는데 MVC 패턴은 양방향 데이터 흐름을 가지고 있어 프로젝트 규모가 커지게 되면 구조가 매우 복잡해지고 예측 불가능한 결과를 나타낼 수 있다. 그래서 생겨난 것이 단방향 데이터 흐름을 가지고 있는 FLUX 패턴이다. FLUX 패턴의 데이터 흐름은 항상 Dispatcher에서 Store로, Store에서 View로, View는 Action을 통해 다시 Dispatcher로 데이터가 흐르게 된다. 단방향 데이터 흐름의 장점은 데이터 변화에 따른 성능 저하 없이 DOM 객체 갱신이 가능하고 데이터 흐름이 단방향이기 때문에 코드를 이해하기 쉽고 데이터 추적과 디버깅이 쉽다. 단점은 변화를 감지하고 화면을 업데이트하는 코드를 매번 작성해야 한다는 단점이 있다.

<br>

- 리덕스 용어와 동작 순서 (https://ivorycode.tistory.com/entry/Redux%EC%9D%98-%ED%9D%90%EB%A6%84%EA%B3%BC-%EC%98%88%EC%A0%9C, https://devlog-h.tistory.com/14)

  (1) 액션 생성 : 액션은 state의 액션을 정의한다. 리듀서는 이 액션을 참고하여 state를 어떻게 변화시킬 지 결정하게 된다.

  액션을 생성하기 위해 첫번째로 액션 타입을 정의하기 위한 액션 타입 변수를 생성한다. 변수의 자료형은 문자열을 사용한다.
  두번째로 액션 크리에이터를 생성한다. 액션 크리에이터는 타입, 페이로드(액션에 필요한 추가 데이터) 등을 포함하는 객체를 반환하는 함수이며
  타입에는 액션 타입을 정의하기 위해 생성한 액션 타입 변수를 할당한다. 또한 액션 크리에이터 함수는 디스패치를 통해 리듀서에 전달되는 함수이다.

  ```js
  // Actions
  const INCREMENT = "INCREMENT";
  const DECREMENT = "DECREMENT";

  // Action Creator
  export const increment = () => {
    return {
      type: INCREMENT,
    };
  };
  export const decrement = () => {
    return {
      type: DECREMENT,
    };
  };
  ```

  (2) 리듀서 생성 : 리듀서는 액션의 결과를 보고 state를 업데이트시켜 반환한다.

  리듀서를 생성하기 위해 첫번째로 state의 초기 값을 정의하기 위한 initialState 변수를 생성한다.
  두번째로 리듀서를 생성하는데 리듀서는 함수로 생성되고 첫번째 인자로 state, 두번쨰 인자로 액션 크리에이터 함수를 전달받는다.
  이 때 첫번째 인자인 state는 미리 생성해놓은 initialState 변수를 할당하여 초기화시키고 리듀서는 컴바인리듀서에서 사용되야하므로 익스포트하여 내보낸다.
  state를 변경은 switch 문을 사용한다. 이 때 case에서 미리 생성해놓은 액션 타입 변수를 사용해서 실행되는 액션을 구분한다.

  ```js
  // 초기값 설정
  const initialState = {
    number: 0,
  };

  // counterReducer
  export default function counter(state = initialState, action) {
    switch (action.type) {
      case INCREMENT:
        return {
          number: state.number + 1,
        };
      case DECREMENT:
        return {
          number: state.number - 1,
        };
      default:
        return state;
    }
  }
  ```

  (3) 컴바인리듀서 생성 : 컴바인리듀서는 모든 리듀서를 하나로 합쳐준다.

  컴바인 리듀서 생성을 위해 필요한 컴바인리듀서 함수, 생성해놓은 리듀서 함수를 임포트한다.
  그 후 컴바인리듀서 함수에 인자로 리듀서 함수를 객체로 전달하고 스토어 생성 시 사용해야하므로 익스포트하여 내보낸다.

  ```js
  export default combineReducers({
    // 리듀서 이름: import한 리듀서
    counterData: counter,
  });
  ```

  (4) 스토어 생성 : 스토어는 state가 저장되는 저장소이다.

  스토어가 가지고 있는 state를 전체 컴포넌트에서 공유하기 위해서 최상위 컴포넌트에 스토어를 연결해야한다.
  스토어 연결을 위해 필요한 크리에이터스토어 함수, 프로바이더 컴포넌트, 컴바인리듀서 함수(네이밍은 rootReducer를 많이 사용)를 임포트한다.
  그 후 store 변수를 생성하여 크리에이터스토어 함수를 할당하는데 인자로 컴바인리듀서 함수를 전달하고
  프로바이더 컴포넌트로 최상위 컴포넌트를 감싸고 프로바이더 컴포넌트 store 프롭스에 store 변수를 할당하여 스토어를 연결할 수 있다.

  ```jsx
  const store = createStore(rootReducer);

  ReactDOM.render(
    <Provider store={store}>
      <App />
    </Provider>,
    document.getElementById("root")
  );
  ```

  (5) 디스패처 생성 : 디스패치는 리듀서에 액션을 전달한다.

  즉, state값을 업데이트할 때는 useDispatch hook을 사용한다.
  useDispatch hook을 사용하기 위해 필요한 useDispatch hook, 액션 크리에이터 함수를 임포트한다.
  그 후 dispatch 변수를 생성하고 useDispatch 함수를 할당하고
  특정 이벤트 리스너가 실행될 때 dispatch 변수에 액션 크리에이터 콜백함수를 인자로 전달하여 state를 업데이트할 수 있다.
  리듀서가 dispatch 변수를 통해 액션을 전달받아 state를 업데이트하게 되는 것이다.

  ```jsx
  export default function Counter() {
    const dispatch = useDispatch();

    return (
      <div>
        <button onClick={() => dispatch(increment())}> + </button>
        <button onClick={() => dispatch(decrement())}> - </button>
      </div>
    );
  }
  ```

  (6) 셀렉터 생성 : 셀렉터는 스토어에 state를 가져온다.

  즉, state값을 사용할 때는 useSelector hook을 사용한다.
  useSelector hook을 사용하기 위해 필요한 useSelector hook을 임포트한다.
  그 후 새로운 변수를 생성하여 변수에 useSelector 함수를 할당하는데 인자로 화살표 함수를 전달한다.
  전달되는 화살표 함수에 파라미터는 state가 되고 리턴 값은 state.리듀서 이름.리듀서 리턴 객체 키 값이 된다.

  ```jsx
  export default function Counter() {
    const count = useSelector((state) => state.counter.number);

    return (
      <div>
        <h4>{count}</h4>
      </div>
    );
  }
  ```

<br>

- 리덕스 미들웨어가 무엇인가?

  리덕스 미들웨어를 사용하면 액션이 디스패치 된 다음, 리듀서에서 해당 액션을 받아와서 업데이트하기 전에 추가적인 작업을 할 수 있다. 보통 리덕스에서 미들웨어를 사용하는 주된 사용 용도는 비동기 작업을 처리 할 때 사용한다. 리덕스 미들웨어 라이브러리로는 redux-thunk, redux-saga, redux-observable, redux-promise-middleware 등이 있다.

<br>

- redux-thunk, redux-saga 설명

  (1) redux-thunk : 특정 작업을 나중에 할 수 있도록 미루기 위해 객체가 아닌 함수 형태의 액션을 디스패치할 수 있게 해준다. 보통 thunk 함수를 사용하여 비동기 처리 시 사용한다.

  ```js
  // 1. 스토어 연결 시 미들웨어 적용
  const store = createStore(
    rootReducer,
    composeWithDevTools(applyMiddleware(ReduxThunk, logger))
  );

  // 액션 생성 함수
  export const increase = () => ({ type: INCREASE });
  export const decrease = () => ({ type: DECREASE });

  // thunk 함수 생성 -> async/await 사용해도 된다.
  export const increaseAsync = () => (dispatch) => {
    setTimeout(() => dispatch(increase()), 1000);
  };
  export const decreaseAsync = () => (dispatch) => {
    setTimeout(() => dispatch(decrease()), 1000);
  };
  ```

  (2) redux-saga : 액션을 모니터링하고 있다가, 특정 액션이 발생하면 이에 따라 특정 작업을 실행할 수 있게 해준다. 제너레이터 문법을 사용한다.

  ```js
  // 참고 : https://react.vlpt.us/redux-middleware/10-redux-saga.html
  // 1. 액션 생성 함수
  export const increaseAsync = () => ({ type: INCREASE_ASYNC });
  export const decreaseAsync = () => ({ type: DECREASE_ASYNC });

  // 2. 사가 생성
  function* increaseSaga() {
    yield delay(1000);
    yield put(increase()); // put은 특정 액션을 디스패치 해준다.
  }

  function* decreaseSaga() {
    yield delay(1000);
    yield put(decrease()); // put은 특정 액션을 디스패치 해준다.
  }

  // 3. 사가의 액션을 모니터링하는 함수 생성
  export function* counterSaga() {
    yield takeEvery(INCREASE_ASYNC, increaseSaga); // 모든 INCREASE_ASYNC 액션을 처리
    yield takeLatest(DECREASE_ASYNC, decreaseSaga); // 가장 마지막으로 디스패치된 DECREASE_ASYNC 액션만을 처리
  }

  // 4. 루트 사가 생성
  export function* rootSaga() {
    yield all([counterSaga()]); // all 은 배열 안의 여러 사가를 동시에 실행시켜준다.
  }

  // 5. 스토어 연결 시 미들웨어 적용
  const sagaMiddleware = createSagaMiddleware(); // 사가 미들웨어를 생성

  const store = createStore(
    rootReducer,
    composeWithDevTools(
      applyMiddleware(
        ReduxThunk.withExtraArgument({ history: customHistory }),
        sagaMiddleware
      )
    )
  );

  sagaMiddleware.run(rootSaga); // 6. 루트 사가를 실행, 이 떄 먼저 연결되어있어야 함
  ```

<br>

- Redux vs MobX vs ContextAPI vs Recoil vs Redux toolkit 비교

  (1) Redux : action, reducer, selector, store를 세팅하는 보일러플레이트 코드는 분명 유지보수에 큰 장점을 가지고 있기도 하지만, 상태의 개수가 적더라도 보일러플레이트 코드가 크기 때문에 불편함이 존재한다. 또한 리덕스의 경우 비동기 데이터 처리를 하기 위해서는 사가와 같은 별도의 라이브러리를 추가적으로 사용해야 한다. 또 데이터 관리에 대해 상당히 보수적인 접근방식을 취하고 있어 높은 러닝커브와 큰 보일러플레이트 코드를 가지고 있지만 확장 및 디버깅에 있어서는 엄청난 강점을 가지고 있다.

  (2) MobX : MobX의 경우 리덕스와 달리 store가 여러 개가 될 수 있어 분리가 용이해 편리할 수도 있는 반면 상태 변경시 다수의 스토어가 영향을 받을 수 있다. 또 리덕스와 다르게 스토어의 데이터를 액션의 발행없이 업데이트 할 수 있는데 구현은 쉽고 용이하지만 테스트나 유지보수의 측면에서는 문제를 일으킬 수도 있다. 그렇기에 장기적인 프로젝트, 유지보수 및 확장성을 고려해야 하는 프로젝트의 경우에는 적합하지 않다. 리덕스에 비해 러닝커브가 낮고 보일러플레이트 코드의 양 또한 적기 때문에 프로젝트의 규모가 크지 않은 경우 사용하기 좋다.

  (3) Context API : Context API는 리액트가 자체적으로 가지고 있다. 정적인 데이터 위주로 처리하거나 업데이트가 빈번하지 않을 때 적합하다. 빈번하고 복잡한 업데이트를 처리 시에는 비효율적이다.

  (4) Recoil : 리코일은 아톰과 셀렉터로 이루어져 있다. 아톰은 상태의 단위로, 유니크한 키값으로 구분된다. 해당 아톰을 구독하고 있으면 해당 컴포넌트들만 선택적으로 리렌더링 된다. 아톰의 상태변화는 순수함수를 통해 일어나는데, 이를 셀렉터라고 한다. 셀렉터에서는 비동기처리 뿐만 아니라 데이터 캐싱 기능도 제공하기 때문에 비동기 데이터를 다루기에도 용이하다. 하지만 상대적으로 최근에 나온 라이브러리이기 때문에 안정성 측면에서는 좋지 못할 수도 있다.

  (5) Redux toolkit : 나는 리덕스 대신 리덕스 툴킷을 사용한다. 리덕스는 큰 보일러 플레이트 코드를 가지고 있어 상태의 개수가 적어도 작성해야 할 코드가 많다. 또 비동기 데이터 처리를 하기 위해 별도의 라이브러리를 추가로 사용해야한다는 단점이 있다. 리덕스 툴킷은 리덕스가 공식적으로 만든 라이브러리로 다양한 내장 기능을 제공하고 있어 패키지 의존성이 적고 보일러 플레이트 코드가 적다는 장점이 있다.

<br>

- redux toolkit 사용법

  (1) store파일을 생성한다. 파일명은 store로 한다. store는 전역 상태 관리가 되는 모든 createSlice를 관리하는 곳이다. store에 reducer에 만들어진 createSlice name을 import해서 넣어줘야한다. 또한 store를 만든 뒤 루트 디렉토리 컴포넌트(ex App컴포넌트)를 Provider 컴포넌트로 감싸 Provider prop를 store={store}로 지정해야한다. 또한 store는 프로젝트에 하나만 존재해야한다.

  ```js
  // store.js
  export const store = configureStore({
    reducer: {
      recommendIndex,
      searchValue,
    },
    devTools: process.env.NODE_ENV !== 'production',
    middleware: (getDefaultMiddleware) => getDefaultMiddleware({ serializableCheck: false }),
  });

  // index.js
  const queryClient = new QueryClient({
    defaultOptions: { queries: { refetchOnMount: false, refetchOnWindowFocus: false } },
  });

  const root = ReactDOM.createRoot(document.getElementById('root') as HTMLElement);
  root.render(
    <React.StrictMode>
      <QueryClientProvider client={queryClient}>
        <Provider store={store}>
          <Routes />
        </Provider>
      </QueryClientProvider>
    </React.StrictMode>
  );
  ```

  (2) createSlice파일을 생성한다. 파일명은 상관없다. 전역 state와 전역 state를 조작하는 함수를 저장할 createSlice를 만들어야한다. 이 createSlice는 프로젝트에 여러 개가 존재할 수 있다. 전역으로 관리 할 state당 하나가 생성되는 것이다.

  (3) createSlice에 initialState는 그냥 state라고 생각하면 된다. 또한 reducers는 이 initialState를 조작할 액션(state값을 조작하는 함수 혹은 state값 재할당 등등 state를 변화시킬 행동)이라고 생각하면 된다.

  ```js
  const recommendIndexSlice = createSlice({
    name: "recommendIndex",
    initialState,
    reducers: {
      increaseIndex(state: INIT_STATE, action: PayloadAction<number>) {
        if (state.index >= action.payload - 1) {
          state.index = 0;
        } else {
          state.index += 1;
        }
      },
      decreaseIndex(state: INIT_STATE, action: PayloadAction<number>) {
        if (state.index < 0) {
          state.index = action.payload - 1;
        } else {
          state.index -= 1;
        }
      },
      resetIndex(state: INIT_STATE) {
        state.index = -1;
      },
    },
  });
  ```

  (4) createSlice에 저장 된 action인 reducers로 state를 업데이트하기 위해서는 useDispatch hook을 사용한다. 디스패치라는 이름에서 알 수 있듯이 파라미터를 담아 보내는 역할을 한다. 파라미터를 보내면 createSlice 내부에 reducers에 전달되어 state를 업데이트 시키는 것이다. 또한 initialState나 업데이트 된 state를 사용할 때는 useSelector hook으로 가져와 사용한다.

  (5) store에 devTools : 환경변수를 이용해서 현재 서버가 개발자모드인지 프로덕션모드인지를 구분해준다. 보통 boolean타입으로 활용하여 구분한다. devTools: process.env.NODE_ENV !== 'production' 과 같이 사용하는데 이 뜻은 로컬에 있는 환경 변수를 사용하면 true가 되면서 개발 모드가 활성화 된다.

  (6) store에 middleware : middleware: (getDefaultMiddleware) => getDefaultMiddleware({ serializableCheck: false }) 와 같이 사용한다. 클라이언트와 서버 중간에 위치해서 중간 기능을 넣는 역할을 한다. getDefaultMiddleware() 는 기본 미들웨어를 적용하기 위해 사용한다. 위와 같이 작성하면 기본 미들웨어에 사용자 미들웨어를 추가하여 함께 사용한다는 뜻이다. 기본 미들웨어는 불변성 검사 미들웨어와 직렬화 기능성 검사 미들웨어가 있다. 불변성 검사 미들웨어는 값을 직접 수정한 경우 (mutation) error를 발생시키는 역할 (redux-immutable-state-invariant)을 하며 직렬화 가능성 검사 미들웨어는 직렬화 할 수 없는 Promise와 같은 객체를 받았을때 error를 발생시키는 역할을 한다.

<br>

- 리덕스가 state를 업데이트시킬때 리액트에서는 해당 상태값을 어떻게 감지하는지?

  dispatch를 통해 변경한 state는 이전의 state와 참조 값이 다르기 때문에 virtualDOM에서 상태가 업데이트 됨을 감지할 수 있다.

<br>

- 어떤 기준으로 상태관리 여부 구분하는지

  부모 컴포넌트에서 state를 props로 넘겨줄 때 props가 2번을 초과하여 내려주어야할 때나 많은 컴포넌트에서 공통적으로 사용해야하는 state같은 경우 전역 상태 관리를 하였다.

<br>

### # **리액트 패턴이란?**

<br>

- 리액트 패턴

  기능만을 담는 컴포넌트와, 뷰만을 담는 컴포넌트로 분리하는 패턴이다. 담당하는 기능이 분리되어 있기 때문에 가독성이 높고, 유지보수가 쉽고 재사용성이 뛰어나다. 또 같은 state를 다른 container에게 props 내림으로 상태를 공유 할 수 있다.

<br>

- 프레젠테이셔널 컴포넌트(present component)

  뷰를 담는 컴포넌트이다. 상태가 없는 컴포넌트(stateless component)라고도 불린다. state를 직접 조작하지 않으며, 컨테이너 컴포넌트가 내려준 props를 사용한다. state 관련 훅을 사용하지 않고 state를 거의 가지지 않으며 만약 state를 가지고 있다면 데이터에 관한것이 아닌 ui 상태에 관한 state를 가지고 있다.

<br>

- 컨테이너 컴포넌트(container component)

  기능을 담는 컴포넌트이다. 상태가 있는 컴포넌트(stateful component)라고도 불린다. 어떤 동작을 하고 어떤 로직을 수행하는지와 관련이 있다. 마크업을 하지 않고 스타일을 사용하지 않는다. 데이터와 데이터 조작에 관한 함수를 만들고 프레젠테이셔널 컴포넌트에 제공한다.

<br>

- 리액트 패턴의 장점

  컨테이너와 프레젠테이셔널 컴포넌트를 나누게 되면 뷰와 로직을 컴포넌트 단위로 나누게 되어 가독성이 높아지고 유지보수가 쉬워진다. 또한 프레젠테이셔널 컴포넌트는 로직과 연관성을 떨어뜨렸기 때문에 재사용이 더욱 쉬워진다. 하지만 뷰와 로직을 무조건 나누어 사용하는 것이 아닌 나누었을 때 재사용할 수 있는 컴포넌트가 아닌 경우나 로직과 UI가 밀접하게 관련이 있는 경우 나누어 사용하는 것이 오히려 가독성이나 유지보수를 어렵게 할 수 있으므로 상황에 맞게 나누어 사용하는 것이 좋다.

<br>

### # **Bundling과 code splitting**

<br>

- 번들링(Bundling)

  서로 연관있는 여러 파일을 하나의 파일로 병합(js, img, scss 등)하는 것을 말한다. 하나로 병합 된 번들로 요청/응답을 받음으로써 HTTP 요청 횟수를 줄일 수 있다. 대표적인 툴로는 웹팩이 있다.

<br>

- 코드스플리팅(code splitting)

  프로젝트 규모가 커지면 번들 사이즈도 커지게 된다. 그렇게 되면 성능 저하가 일어날 수 있다. 이럴 때 코드 스플리팅을 사용한다. 코드 스플리팅은 하나의 번들을 여러 개의 번들로 나누어준다. 코드스플리팅으로 번들을 나눈 후 실제 로드될 화면에 필요한 번들 파일만 불러오고 나머지 번들 파일은 호출하지 않고 지연시키는 비동기 로딩으로 로딩 속도를 향상시킬 수 있다.

<br>

- react에서의 코드 스플리팅 방법

  (1) dynamic import 문법 사용 : 자바스크립트 함수 비동기 로딩 시 import() 함수 형태로 메서드 안에서 사용하게 되면 필요할 때 해당 스크립트를 불러와서 사용할 수 있다. import를 함수로 사용하면 Promise를 반환한다.

  ```js
  const onClick = () => {
    import("./subPage").then((result) => result.default());
  };
  ```

  (2) React.lazy와 Suspense를 통한 컴포넌트 코드 스플리팅 : React.lazy는 컴포넌트를 렌더링하는 시점에서 비동기적으로 로딩할 수 있게 해 주는 유틸 함수이다. 또한 lazy로 코드 스플리팅 된 컴포넌트는 Suspense를 통해 나타낼 수 있다. Suspense는 리액트 내장 컴포넌트로 코드 스플리팅 된 컴포넌트를 로딩하도록 발동시킬 수 있고, 로딩이 끝나지 않았을 때 fallback 이라는 props를 통해 로딩 중에 보여줄 요소를 지정할 수 있다. 또한 react-loadable 라이브러리의 Lodable Components를 사용하는 방법도 있다.

  ```jsx
  const Home = lazy(() => import("./routes/Home"));
  const About = lazy(() => import("./routes/About"));

  const App = () => (
    <Router>
      <Suspense fallback={<div>Loading...</div>}>
        <Switch>
          <Route exact path="/" component={Home} />
          <Route path="/about" component={About} />
        </Switch>
      </Suspense>
    </Router>
  );
  ```

  (3) Webpack에 Entry Point 설정 : Entry Point는 웹팩이 앱에서 번들링하려는 모듈의 진입 파일이다. 리액트 앱이 여러 엔트리 포인트를 설정한다면 각각의 엔트리 포인트 마다 코드 스플리팅이 가능하다. webpack.config.js에 entry 프로퍼티를 작성하면 웹팩에서 자동으로 entry 프로퍼티 내부에 엔트리 포인트를 다른 chunk로 관리하여 로딩한다.

  ```js
  // webpack.config.js
  const path = require("path");

  module.exports = {
    mode: "development",
    entry: {
      index: "./src/index.js",
      another: "./src/another-module.js",
    },
    output: {
      filename: "[name].bundle.js",
      path: path.resolve(__dirname, "dist"),
    },
  };
  ```

<br>

### # **React Native**

<br>

- 리액트 네이티브 개발을 해본 적이 있는지

  부트캠프 교육 시 한달 정도 기업협업에 나가 경험해 본 경험이 있다. react native, typescript, mobx 등의 기술을 사용했었다. 마일리지를 이용하여 기프티콘을 구매하는 서비스였는데 기능을 추가하는 작업을 했었다. 카카오맵API, 웹뷰를 활용하여 지도 주소 검색 기능, 지번 도로명 주소 변환, 새 페이지 추가, 작은 버그 수정 등의 작업을 했었다.

<br>

- 웹뷰

  웹뷰는 모바일 앱 어플리케이션의 일부 부분 및 페이지를 웹 어플리케이션 및 웹 페이지로 제공하는 기능을 말한다. 안드로이드와 iOS 모두에서 제공하고 있다. 웹뷰를 사용한 장점은 배포 주기를 빠르게 가져갈 수 있다는 점이다.

<br>

- 웹뷰 사용 경험

  웹뷰에 보여질 카카오 map api, 버튼 등을 생성하여 프로젝트를 따로 만들어 준 뒤 배포하고 웹뷰를 생성할 프로젝트에서 WebView 컴포넌트와 WebView 컴포넌트의 source 옵션을 통해 배포된 프로젝트와 연결하고 다른 옵션들을 통해 웹뷰에서 받은 주소 데이터를 저장하고, 로딩 시 스피너를 구현하였다.

<br>

### # **Progressive rendering이란 무엇인가요?**

<br>

- 서버에서 중요한 컨텐츠를 렌더링한 후, 중요하지 않은 콘텐츠를 기다리지 않고 클라이언트로 스트리밍하는 기술이다. 그런 다음 서버에서 렌더링되면 나중에 중요하지 않은 콘텐츠를 스트리밍한다. 관련 기술로는 Image Lazy Loading, DOMContentLoaded 이벤트의 사용 등이 있다.

<br>

### # **JSX(JavaScript XML)**

<br>

- JSX는 Javascript에 XML을 추가하여 확장한 문법이다. 공식적인 자바스크립트 문법은 아니며 브라우저에서 실행하기 전 번들링 과정 중 바벨을 사용하여 일반 자바스크립트로 변환된다. JSX문법의 사용은 react의 특징 중 하나이다.

<br>

### # Link, NavLink, useNavigate 차이

<br>

- Link

페이지 이동 시 사용

<br>

- NavLink

페이지 이동 시 사용, Link 와의 차이점은 자체적으로 boolean을 반환하는 isActive 속성을 가지고 있으며 NavLink 컴포넌트 to 프로퍼티에 할당 된 url로 이동 시 isActive는 true가 된다. 이 boolean 값을 사용하여 페이지로 이동 시 스타일을 동적으로 변경시켜줄 수 있다.

<br>

- useNavigate

페이지 이동 시 사용하는 hook, 페이지 이동 시 추가 로직을 사용할 수 있다. 또 이동되는 페이지에 state를 전달할 수 있다.
또 해당 페이지를 새로 불러오거나, 이전 페이지, 다음 페이지로의 이동을 편하게 할 수 있다. `ex) navigate(0), navigate(-1), navigate(+1)`

<br>

### # **비즈니스 로직을 리액트를 사용 시 어떻게 모듈화시키는게 좋은지?**

<br>

- 일단 전체적인 구조는 뷰와 로직을 분리하는 것이 가장 좋다고 생각한다. render 함수 안 렌더단에서는 컴포넌트를 적극적으로 활용하여 가독성을 최대한으로 끌어올리고 로직이 최대한 들어가지 않도록 작성하는 것이 중요하고 render 함수 외부에 로직이 집중되도록 작성하는 것이 중요하다고 생각한다. 또한 로직단에서도 중복 로직이나 너무 긴 로직의 경우 hook으로 빼서 사용하여 가독성을 높이는 것이 중요하다고 생각한다. 또한 비지니스 로직 같은 경우에도 관심사 별(서버 통신 관련, 돔 조작 관련, state 관련, 이벤트 핸들러 등)로 로직을 나누고 공통 로직인지 개별 로직인지 구분하여 컴포넌트 내부에 작성하거나 별도로 파일을 만들어 관리하는 것이 좋다. 공통 로직의 경우 별도로 파일을 만들어 관리하고 필요한 컴포넌트 내부에서 import 하여 사용하는 방식이다.

<br>

### # **성능을 측정해 본 적이 있는지, 어떤 방법을 사용해보았는지?**

<br>

- 함수 성능 측정

  perpomance.now, console.time

<br>

- 컴포넌트 렌더링 속도 및 리렌더링 측정

  react developer tools 크롬 익스텐션 설치 후 개발자 도구에 profiler탭 활용 (ms 단위)

<br>

- 웹 페이지 퍼포먼스, 웹접근성, SEO, 표준 모범 사례를 따르고 있는지 확인하는 Best Practices 측정

  개발자 도구에 Lighthouse탭 활용

<br>

### # **lighthouse을 활용한 사이트 퍼포먼스 측정**

<br>

- 크롬 개발자 도구에 lighthouse를 사용하여 사이트 퍼포먼스를 측정해보았다. 실제 성능을 측정하는 Performance, 웹과 네이티브 앱의 이점을 모두 가진 서비스인지 체크하는 Progressive Web App, 웹 접근성을 측정하는 Accessibility, 검색 엔진 수집 최적화를 측정하는 SEO 등이 있다.

<br>

### # **useMemo, useCallback에 대한 설명**

<br>

- 메모제이션이란?

  일단 useMemo와 useCallback에서는 메모이제이션이라는 개념이 나오는데 메모이제이션이란 이전 값을 메모리에 저장해두어 동일한 계산의 반복을 제거해 빠른 처리를 가능하게 하는 기술이다. useMemo는 메모이제이션 된 값을 반환하고 useCallback은 메모이제이션 된 함수를 반환한다. useMemo와 useCallback은 의존성 배열에 넘겨준 값이 변경되었을 때만 메모리제이션된 값을 다시 계산하고 아닌 경우 동일한 값을 반환한다.

<br>

- useMemo와 useCallback은 언제 사용하는가?

  useMemo와 useCallback을 사용하는 경우는 단순하게 의존성 배열이 적은 경우 useMemo와 useCallback으로 래핑하여 사용하고 있다. 의존성 배열이 적은 경우 값의 변화가 많지 않다는 것이기 때문에 캐싱하여 사용하는 것이 효율적이다. 하지만 의존성 배열이 많은 경우 값의 변화가 많다는 것이기 때문에 캐싱하여 사용할 필요가 없다. 즉 의존성 배열은 적은데 함수 내부에서 계산하는 로직이 많아질수록 useMemo, useCallback을 사용하고 있다.

<br>

### # **HOC(High Order Component)가 무엇인지 아는지?**

<br>

- HOC(High Order Component)는 고차 컴포넌트이며 다른 컴포넌트를 감싸는 리액트 컴포넌트다. 리액트 컴포넌트를 인자로 받아서 새로운 리액트 컴포넌트를 반환하는 함수로 볼 수 있다. 비지니스 로직을 담당하는 컨테이너 컴포넌트와 뷰를 담당하는 프레젠테이셔널 컴포넌트를 분리하여 사용 할 때, 컨테이너 컴포넌트를 고차 컴포넌트로 만들어서 사용한다.

  ```jsx
  const withHOC = (WrappedComponent) => {
    const newProps = {
      loading: false,
    };
    return (props) => {
      return <WrappedComponent {...props} {...newProps} />;
    };
  };
  ```

<br>

### # **컴포넌트와 엘리먼트의 차이점은?**

<br>

- 엘리먼트

  DOM element(태그)를 나타내는 일반적인 객체

<br>

- 컴포넌트

  props를 받아 Elements를 출력하는 함수 혹은 클래스이다. react에서 index 파일 내부 ReactDOM.createRoot 함수를 통해 container DOM을 지정하고 컴포넌트에 render 함수를 통해 엘리먼트를 반환하여 container DOM에 렌더링한다.

<br>

### # **useEffect에서 unmount 하는 방법**

<br>

- useEffect에 의존성 배열을 넣지 않은 빈 의존성 배열을 넣은 상태에서 return 값을 지정하게 되면 componentWillUnmount 역할을 할 수 있다. 만약 의존성 배열을 넣은 후 return 값을 지정하게 되면 의존성 배열이 바뀌기 전 사이드 이펙트를 실행할 수 있다.

<br>

### # **useEffect와 useEffectLayout 차이**

<br>

- 둘의 사용법은 완전히 동일하다. useEffect는 componentDidMount와 componentDidUpdate와는 다르게 DOM이 화면에 그려진 후 호출된다. 예를 들어 useEffect 내부에서 state를 업데이트하여 DOM에 내용을 채운다고 가정했을 때 DOM을 렌더링 한 후 useEffect를 호출하여 state를 업데이트하고 리렌더링을 수행하여 DOM에 내용을 채우는 것이다. 하지만 DOM에 갯수가 많아지고 복잡해지면 렌더링 시간이 증가하게 되어 useEffect 사용 시 state가 업데이트 되지 않은 상태를 사용자가 볼 위험이 생긴다. 그래서 생겨난 것이 useEffectLayout 이다. useEffectLayout은 useEffect와는 다르게 DOM을 그리기 전 이벤트를 수행한다.

  ```
  // useEffect
  (1) `<div>그의 이름은 이며, 나이는 0살 입니다.</div>` 를 페인트
  (2) useEffect 이펙트 내부의 setAge(31), setName("재민") 호출
  (3) 재렌더링 수행 -> `<div>그의 이름은 재민이며, 나이는 31살 입니다.</div>`

  // useEffectLayout
  (1) useEffectLayout 이펙트 내부의 setAge(31), setName("재민") 호출
  (2) 재렌더링 수행 -> `<div>그의 이름은 재민이며, 나이는 31살 입니다.</div>`
  ```

<br>

### # useReducer가 무엇인가?

<br>

- useReducer

  useReducer는 useState와 같이 state를 관리하고 업데이트할 수 있는 hook이다. useState와의 차이는 예를 들어 컴포넌트에서 관리하는 값이 딱 하나고, 그 값이 단순한 숫자, 문자열 또는 boolean 값이라면 확실히 useState 로 관리하는게 편할 수 있고 만약에 컴포넌트에서 관리하는 값이 여러개가 되어서 상태의 구조가 복잡해진다면 useReducer로 관리하는 것이 편할 수 있다.

  ```jsx
  import { useReducer } from "react";

  function reducer(state, action) {
    switch (action.type) {
      case "INCREMENT":
        return state + 1;
      case "DECREMENT":
        return state - 1;
      default:
        return state;
    }
  }

  function App() {
    const [number, dispatch] = useReducer(reducer, 0);

    const onIncrease = () => {
      dispatch({ type: "INCREMENT" });
    };

    const onDecrease = () => {
      dispatch({ type: "DECREMENT" });
    };

    return (
      <div>
        <h1>{number}</h1>
        <button type="button" onClick={onIncrease}>
          +1
        </button>
        <button type="button" onClick={onDecrease}>
          -1
        </button>
      </div>
    );
  }
  ```

<br>

- useReducer의 장점

  useReducer는 로직을 분리하여 재사용성을 높이고 setState를 여러번 사용하지 않아도 된다는 장점이 있다.

<br>

- useReducer 사용법

  useReducer의 사용법으로는 useReducer의 첫번째 인자로 reducer 함수, 두번째 인자는 초기값을 넣어준다. 첫번째 인자로 넘어오는 reducer 함수 내부에 switch문으로 액션을 정의하고 dispatch를 통해 reducer 함수 내부에 case를 비교하여 액션을 실행시킨다.

<br>

### # **SVG를 스타일링하는데 익숙하신가요?**

<br>

- 제가 진행한 프로젝트에서는 SVG 스타일링을 위해 SVG를 컴포넌트화하여 사용하였습니다. 컴포넌트화를 통해 하나의 svg 파일로 다양한 크기, 색상을 가진 아이콘으로 다양하게 활용할 수 있었습니다.

<br>

### # **렌더함수 안에서 hooks를 사용하면 안되는 이유?**

<br>

- react 공식 문서에 나와있는 이유로는 최상위에서만 hook을 호출해야 컴포넌트가 렌더링 될 때마다 항상 동일한 순서로 Hook이 호출되는 것이 보장된다고 한다. 예를 들어 useEffect의 경우 DOM의 렌더링 이후 실행되는데 만약 렌더 함수 스스로 useEffect를 실행하게 되면 이 useEffect와 관련 된 DOM이나 함수들이 보장할 수 없는 값들을 출력할 수 있다. 그렇기 때문에 렌더 함수 외부에 hook을 호출하여 react가 권장하는 순서대로 DOM의 렌더링과 hooks이 동작할 수 있도록 해야한다.

<br>

### # **리액트는 어떻게 렌더링되죠?**

<br>

(1) ReactDOM.render(루트 엘리먼트, DOM 노드) 호출

(2) 루트 엘리먼트부터 시작해서 마주친 엘리먼트의 타입을 검사하여 업데이트가 필요한 컴포넌트를 찾는다.

(3) 업데이트가 필요한 컴포넌트를 만나면 props를 제공하여 새로운 엘리먼트 트리를 얻는다.

(4) 버츄얼 돔을 통해 새로운 엘리먼트 트리를 이전 엘리먼트 트리와 비교하여 일괄적으로 업데이트 시킨다.

이러한 과정을 두 단계로 나누어 표현하는데

(1) 렌더 페이즈(Render phase): 컴포넌트를 렌더링하고 변경사항을 계산하는 모든 작업

(2) 커밋 페이즈(Commit phase): 돔에 변경사항을 적용하는 과정

으로 나누어 표현한다.

<br>

### # **커스텀 훅 사용 이유**

<br>

- 관심사의 분리, 여러 컴포넌트에서 공통적으로 사용하는 함수의 경우, 한 컴포넌트 내에 코드 길이 줄이기 위해 커스텀 훅을 사용하고 있다.

<br>

### # **로그인 버튼을 누른 후 처리가 지연 되고 있는 순간에 다른 UI 버튼을 클릭한다면 처리는 어떻게 되는가? 비동기 처리라고 한다면 이건 문제가 있지 않은가?**

<br>

- 대부분 로그인이 필요한 서비스의 경우 로그인 하지 않은 사용자가 UI를 조작하게 되면 로그인 페이지로 리다이렉트 시키는데 만약 비동기 통신을 통해 액세스 토큰을 받아오는 로그인 과정이 지연되는 경우 스피너같은 로딩 화면을 띄워 토큰을 받아오기 전 사용자가 다른 UI를 누를 수 없도록 방지할 것 같다.

<br>

### # **무작위 데이터 테스트는 어떻게 하시나요?**

<br>

- 제이슨 제너레이터(https://json-generator.com/)와 같은 무작위 더미데이터를 생성해주는 사이트를 활용하여 무작위 데이터를 만든 뒤 테스트를 진행할 수 있을 것 같다.

<br>

### # **제어 컴포넌트와 비제어 컴포넌트 차이**

<br>

- 제어 컴포넌트

  컴포넌트의 state나 props로 입력 폼 값이 제어되는 컴포넌트이다. 예시로 input의 value 값을 useState로 값을 업데이트 시키는 것이 대표적인 제어 컴포넌트의 예시이다. 데이터와 UI가 항상 동기화되어 입력 값 발생 시 계속 리렌더링 되어 최신화가 유지된다. 유효성 검사나 조건부 버튼 활성화에 사용한다.

  ```jsx
  export default function App() {
    const [input, setInput] = useState("");
    const onChange = (e) => {
      setInput(e.target.value);
    };

    return (
      <div className="App">
        <input onChange={onChange} />
      </div>
    );
  }
  ```

<br>

- 비제어 컴포넌트

  DOM 자체에서 입력 폼 데이터를 다루는 컴포넌트이다. 예시로 input에 ref 속성을 할당하여 입력 폼을 제출할 때 값을 업데이트 시키는 것이 대표적인 비제어 컴포넌트의 예시이다. 데이터와 UI가 동기화되어 있지 않아 입력 값 발생 시 리렌더링 되지 않고 입력 폼을 제출할 때 렌더링된다. 일회성 정보 검색이나 제출 시 값 검증에 사용한다.

  ```jsx
  export default function App() {
    const inputRef = useRef();
    const onClick = () => {
      console.log(inputRef.current.value);
    };

    return (
      <div className="App">
        <input ref={inputRef} />
        <button type="submit" onClick={onClick}>
          전송
        </button>
      </div>
    );
  }
  ```

<br>

### # **리액트의 렌더링 성능 향상을 위해 어떻게 해야 하나?**

<br>

(1) 렌더링 성능 측정 : react developer 익스텐션이나 lighthouse 를 활용하여 렌더링 성능을 측정하고 perpomance API나 console.time 메소드를 활용하여 함수 성능을 측정하고 개선한다.

(2) useMemo, useCallback : useMemo, useCallback 등을 사용하여 값이나 함수를 메모이제이션 해 사용한다.

(3) 코드 스플리팅 : Lazy와 Suspense를 사용하여 코드 스플리팅하고 번들의 크기를 줄여 당장 필요한 컴포넌트만 우선적으로 렌더링하도록 한다.

(4) 이미지 사이즈 최적화 : 이미지를 압축율이 좋은 이미지 포맷으로 변경하거나 사용자에게 보여지는 크기를 고려하여 사이즈를 줄인다. 또한 고정 사이즈를 사용하여 리플로우를 최소화할 수 있다.

(5) 이미지 레이지 로딩 : IntersectionObserver API와 같이 뷰포트를 감지하는 API를 활용하여 해당 이미지 보여져야 할 때 서버에 요청을 보내 이미지를 가져온다.

(6) 애니메이션 최적화 : 애니메이션은 리플로우와 리페인트를 발생시키는 원인이다. witdh와 같은 크기를 직접적으로 변경하는 애니메이션의 경우 cpu에서 처리하게 되는데 transform의 scale을 활용하여 크기를 변경시키는 경우 gpu에서 처리하게 되므로 성능 향상에 도움이 된다.

(7) 웹폰트 경량화 : 사용할 글자만 남겨놓은 서브셋 파일을 활용하여 웹폰트 파일의 크기를 줄인다.

(8) state와 props변경 최소화 : state와 props의 변경을 최소화하여 리렌더링을 최소화한다.

(9) 프롭시 드릴링(props drilling) 피하기 : 부모 컴포넌트에서 자식 컴포넌트로 전달하는 프롭스의 깊이가 깊어질수록 성능에 좋지 않다. 부모의 state가 변경되면 자식 컴포넌트 모두 리렌더링되기 때문이다. 개인적으로 2번 이상 넘겨주지 않도록 기준을 정해서 작업하고 있다. 넘어가는 경우 전역 상태 관리 라이브러리를 사용하여 해결할 수 있다.

(10) state의 분할 : 한 컴포넌트에 state를 몰아서 사용하는 경우 state 변화가 빈번하게 발생할 수 있기 때문에 state를 사용하는 컴포넌트 내부에 작성할 수 있도록 한다. 또한 객체 형태의 state의 경우 객체 프로퍼티 중 하나만 사용하는 컴포넌트가 있거나 하는 경우 분리해서 사용하는 것이 좋다.

<br>

### # **key는 어떻게 사용되나요?**

<br>

- index값은 사용하지 않는다. 만약 배열의 순서가 수정될 경우 중복되는 key값이 발생할 수 있기 때문이다. 그렇기 때문에 유니크한 값을 사용하기 위해 map 메소드를 사용한 배열 요소가 id값을 가지고 있다면 id값을 사용하도록 하고 있다. id값이 존재하지 않다면 가지고 있는 다른 유니크한 값을 사용하거나 배열 요소 자체를 문자열로 변환 후 조합하여 사용하기도 한다.

<br>

### # **prop drilling은 무엇이고 어떻게 피할 수 있나요?**

<br>

- prop drilling은 부모 컴포넌트에서 하위 컴포넌트로 props를 전달하는 것을 과정을 말한다. prop drilling이 깊어지게 되면 해당 props의 추적이 어려워져 유지보수가 힘들어지고 실제 props를 사용하는 컴포넌트 사이에 props를 사용하지 않는 컴포넌트도 포함될 수 있다. 또한 부모에 props가 변경되면 하위 컴포넌트들도 모두 리렌더링 되기 때문에 성능 저하에 원인이 될 수 있다. 그렇기 떄문에 prop drilling을 최대한 피해주는 것이 좋은데 prop drilling을 피하는 방법으로는 대표적으로 전역 상태 관리 라이브러리를 사용하거나 컴포넌트를 잘게 쪼개지 않고 가장 가까운 부모 컴포넌트와 props를 공유할 수 있도록 유도하는 것이다.

<br>

### # **얕은 비교(shallow equal)와 깊은 비교(deep equal)에 대해서 설명해주세요.**

<br>

- 얕은 비교

  얕은 비교는 실제 내부 값까지 비교하는 것이 아닌 참조하는 값에 메모리 주소를 비교한다.

<br>

- 깊은 비교

  객체 내부 값까지 비교한다.

<br>

- 의존성 배열은 얕은 비교, 깊은 비교 중 무엇을 하게 되나요?

  의존성 배열은 얕은 비교를 수행한다. 동일한 참조인지 확인하여 동일한 참조가 아닌 경우 의존성 배열에 변화가 생겼다고 감지하여 해당 hook을 실행하게 된다.

<br>

### # **리액트의 에러바운더리에 대해 아시나요?**

<br>

- react-error-boundary 패키지를 설치한 후 ErrorBoundary 컴포넌트를 사용할 수 있는 것으로 알고 있다. ErrorBoundary 컴포넌트를 사용하면 런타임 시 문제가 발생할 경우 ErrorBoundary 컴포넌트에 fallback 속성에 jsx문법이나 컴포넌트를 할당하여 에러 페이지를 노출시킬 수 있다. 또한 useQuery와 함께 사용할 경우 useQuery 옵션 중 useErrorBoundary 옵션을 true로 설정하면 useQuery에 isError를 ErrorBoundary로 대체하여 사용할 수 있다.

<br>

### # **리액트 라우터같은 Client Side Routing 에 대해서 설명하세요.**

<br>

- 라우팅은 사용자가 웹사이트의 다른 페이지로 이동하는 프로세스를 말한다. 클라이언트 사이드 라우팅은 클라이언트 측에서 라우팅하는 것을 말하며 클라이언트 사이드 라우팅의 원리로는 HTML5 History API의 pushState라는 메소드를 이용해 임의의 히스토리 기록을 만들어서 이동하는 것이다. 즉 실제 페이지로 이동하는 것이 아닌 history api가 만들어낸 페이지로 이동하는 것이다. 클라이언트 사이드 라우팅의 특징으로는 렌더링되는 데이터의 양이 적기 때문에 구성 요소 간 라우팅의 속도가 빠르고 별도의 페이지가 렌더링 되는 것이 아니기 때문에 새로 고침되지 않는 특징이 있다.

<br>

### # **react-query**

<br>

- react-query란?

  react-query 라이브러리는 비동기 통신을 위한 라이브러리이다. react-query를 통해 받아온 데이터는 캐싱할 수 있고 캐싱 된 데이터는 재요청하지 않고 key값을 통해 컴포넌트 간 공유할 수 있고, retry와 같은 옵션을 사용하여 요청 실패 시 재요청 횟수를 지정하여 재요청을 시도할 수 있고, enable과 같은 옵션을 활용하여 삼항연산자나 조건을 할당하여 조건에 맞는 시기에 api를 호출할 수 있다는 장점이 있다. 또한 기본적으로 제공하는 data, isLoad, isError 등을 통해 데이터나 예외 처리를 쉽게 할 수 있으며 이 외에도 많은 옵션을 제공하여 편리하게 api 호출을 최적화 할 수 있다는 장점이 있다.

<br>

- staleTime

  데이터가 fresh 상태로 유지되는 시간을 지정한다. fresh 상태일 때는 해당 데이터를 재요청하지 않는다. stale 상태가 되는 경우 캐싱 데이터와 무관하게 재요청하여 최신 데이터 상태를 유지하도록 한다.

<br>

- cacheTime

  데이터가 캐싱되는 시간을 결정한다. 시간이 지나면 가비지 콜렉터로 수집된다.

<br>

- enable

  enable 내부에 삼항연산자나 조건을 할당하여 조건에 맞는 시기에 호출할 수 있다.

<br>

- useMutation

  useQuery가 데이터를 조회할 때 사용한다면 useMutation은 데이터를 생성, 업데이트, 삭제 할 때 사용 된다. onSuccess(성공 시), onError(실패 시), onSettled(성공실패 상관없이) 속성을 활용하여 데이터 처리 후 액션을 처리할 수 있다.

  ```js
  const queryClient = useQueryClient(); // 등록된 quieryClient 가져오기

  const savePerson = useMutation(
    (person: Iperson) => axios.post("http://localhost:8080/savePerson", person),
    {
      onSuccess: () => {
        // 요청이 성공한 경우
        console.log("onSuccess");
        queryClient.invalidateQueries("persons"); // queryKey 유효성 제거
      },
      onError: (error) => {
        // 요청에 에러가 발생된 경우
        console.log("onError");
      },
      onSettled: () => {
        // 요청이 성공하든, 에러가 발생되든 실행하고 싶은 경우
        console.log("onSettled");
      },
    }
  ); // useMutate 정의
  ```

<br>

### # **React batch update**

<br>

- 싱글 페이지 애플리케이션의 클라이언트 사이드 렌더링의 경우 자바스크립트를 통해 동적으로 dom을 조작하는데 이 때 잦은 상태 변화가 일어나게 된다. 상태 변화가 일어나는 시점마다 렌더링을 발생시키면 성능 이슈가 발생할 수 있어 react는 batch update를 16ms 단위로 진행한다. 즉 16ms동안 변경 된 상태 값들을 모아서 단 한번 리렌더링을 진행한다. 하지만 이렇게 state가 비동기적으로 동작함으로써 원하는 결과 값을 얻지 못하는 경우가 생긴다. 이 때 prevState같은 updater 함수를 사용하여 비동기로 동작하는 state를 동기적으로 동작하게 할 수 있다. setState()의 인자로 함수를 전달하는것을 함수형 setState라고 하는데 함수형 setState를 사용하면 리액트가 state를 변경하기 위해 setState의 변경 내용을 합치는 것이 아니라 하나의 큐(queue)에 setState를 올리고 이것들이 호출된 순서에 따라 state를 변경하게 된다. 이 때 updater의 인자로 state를 넣어주면 updater 인자 state는 항상 최신 상태로 유지하기 때문에 state가 동기적으로 업데이트 된다.

<br>

### # **동적 라우팅**

<br>

- react-router-dom에 Route 컴포넌트에 path 경로를 콜론 뒤에 변수로 지정하고 아이템 리스트에서 리스트 클릭 시 해당 아이템에 유니크한 id값을 path 경로로 지정해주어 동적 라우팅을 구현하였다.

  ```jsx
  // Router.js
  <Route path="/productDetail/:id" element={<ProductDetail />} />;

  // ProductList.js
  const goToDetail = (productId) => {
    navigate(`/productDetail/${productId}`);
  };
  ```

<br>

### # **페이지 네이션 구현 방법**

<br>

- 한 페이지에 보여 줄 데이터 수, 페이지 넘버 등의 정보가 담겨있는 쿼리 스트링을 백엔드와 지정하여 맞춘 뒤 url에 useSearchParams와 같은 hook을 이용하여 url에 백엔드와 맞춘 쿼리 스트링이 포함되도록 지정하고 이전 페이지나 다음 페이지로 이동 시 url의 포함 된 쿼리 스트링을 useLocation과 같은 hook으로 가져온 뒤 location에 search key에 접근하여 해당 데이터를 요청하면 페이지 네이션을 구현할 수 있을 것 같다.

<br>

### # **디자인 패턴** (https://velog.io/@iamjoo/mvc-mvp-mvvm-flux-%EB%94%94%EC%9E%90%EC%9D%B8-%ED%8C%A8%ED%84%B4-86ocg4bf)

<br>

- MVC 패턴

  - 구조 : 모델, 뷰, 컨트롤러

    (1) 모델 : 데이터와 그 데이터(내부 비지니스 로직)를 처리하는 부분

    (2) 뷰 : 사용자에서 보여지는 UI 부분

    (3) 컨트롤러 : 사용자의 입력을 받고 모델과 뷰에 중간 역할을 함

  - 동작

    ![mvc](https://user-images.githubusercontent.com/85284246/178215067-a4f2ddbe-0f4a-41be-9683-e22f62d37771.png)

    (1) 사용자의 액션들은 컨트롤러에 들어오게 된다.

    (2) 컨트롤러는 사용자의 액션을 확인하고, 모델을 업데이트한다.

    (3) 컨트롤러는 모델을 나타내줄 뷰를 선택한다.

    (4) 선택 된 뷰는 업데이트 된 모델을 이용하여 화면을 나타낸다.

  - 장점 : 패턴의 사용이 단순하다.

  - 단점 : 뷰와 모델 사이의 의존성이 높다. 높은 의존성 때문에 어플리케이션이 커질수록 복잡하지고 유지보수가 어렵게 만들 수 있다.

<br>

- MVP 패턴

  - 구조 : 모델, 뷰, 프레젠터

    (1) 모델 : 데이터와 그 데이터(내부 비지니스 로직)를 처리하는 부분

    (2) 뷰 : 사용자로부터의 입력을 받고 사용자에게 보여지는 UI부분을 표시

    (3) 프레젠터 : 뷰와 모델 사이에 자료 전달 역할

  - 동작

    ![mvp](https://user-images.githubusercontent.com/85284246/178215069-6c1d8fb3-201e-4d31-b138-b4b1457cca66.png)

    (1) 사용자의 액션들은 뷰를 통해 들어오게 된다.

    (2) 뷰는 데이터를 프레젠터에 요청한다. 이 때 관계는 1대1 관계이다.

    (3) 프레젠터는 모델에게 뷰 업데이트에 필요한 데이터를 요청한다.

    (4) 모델은 프레젠터에게 요청받은 데이터를 응답한다.

    (5) 프레젠터는 뷰에게 데이터를 응답한다.

    (6) 뷰는 프레젠터가 응답한 데이터를 이용하여 화면을 나타낸다.

  - 장점 : 프레젠터를 통해서만 데이터를 전달 받기 때문에 뷰와 모델의 의존성이 없다.

  - 단점 : 뷰와 프레젠터 사이의 의존성이 높다.

<br>

- MVVM 패턴

  - 구조 : 모델, 뷰, 뷰모델

    (1) 모델 : 데이터와 그 데이터(내부 비지니스 로직)를 처리하는 부분

    (2) 뷰 : 사용자로부터의 입력을 받고 사용자에게 보여지는 UI부분을 표시

    (3) 뷰모델: 뷰와 모델 사이에 매개체 역할

  - 동작

    ![mvvm](https://user-images.githubusercontent.com/85284246/178215072-2a197512-1d58-458d-8bef-3893678a5bef.png)

    (1) 사용자의 액션들은 뷰를 통해 들어오게 된다.

    (2) 뷰는 데이터를 뷰모델에 요청한다.

    (3) 뷰모델은 모델에게 뷰 업데이트에 필요한 데이터를 요청한다.

    (4) 모델은 뷰모델에게 요청받은 데이터를 응답한다.

    (5) 뷰는 뷰모델과의 데이터 바인딩(데이터를 묶어 동기화시킨다)을 이용해 화면을 갱신한다.

  - 장점 : 뷰와 모델 사이의 의존성이 없고 뷰모델은 모델하고만 소통을 하고 데이터만 관리하는 방식으로 뷰와의 의존성을 없앴다.

  - 단점 : 뷰모델의 설계가 어렵다.

<br>

- FLUX 패턴 : MVC 패턴의 양방향 데이터 흐름은 애플리케이션의 규모가 커질수록 데이터 흐름을 파악하기가 어렵고 복잡도가 증가한다는 문제가 발생한다. 그래서 나온 것이 단방향 데이터 흐름의 FLUX 패턴이고 FLUX 패턴의 일부분을 적용시킨 것이 리덕스와 몹엑스이다.

  - 구조와 동작순서 : 액션, 디스패처, 스토어, 뷰(컨트롤러 뷰)

    ![flux](https://user-images.githubusercontent.com/85284246/178215058-06245ee4-fa91-46ce-9497-c21dc423131b.png)

    (1) 액션 : 액션 생성자를 통해 디스패처에게 액션 객체를 전달한다.

    (2) 디스패처 : 액션 객체를 받아 액션 객체의 타입을 정의하여 스토어에 전달한다.

    (3) 스토어 : 액션 객체 타입을 받아 참고하여 상태를 업데이트 시키고 상태를 저장한다.

    (4) 뷰 : 컨트롤러 뷰는 스토어의 상태 변경 시 스토어의 데이터를 가져와 자식 뷰에게 분배한다.

  - 장점 : 단방향 데이터 흐름으로 데이터 흐름을 파악하기 쉽기 때문에 예상하지 못한 에러를 방지할 수 있다.

  - 단점 : FLUX 패턴을 적용한 라이브러리는 비교적 러닝 커브가 높은 편이다.

<br>

### # **웹사이트 scrolling 성능을 향상시키기 위한 몇가지 방법에 대해 설명해보세요.**

<br>

- 스크롤 이벤트의 특성 상 반복적으로 이벤트를 호출되게 되는데 반복적으로 호출되는 이벤트의 경우 클린업 함수를 통해 클리어 처리가 필요하다. removeEventListener를 통해 클린업 함수를 만들어 클리어 처리를 해주어야 메모리 누수가 발생하지 않는다. 또한 스크롤 이벤트의 경우 쓰로틀링을 구현하여 일정 시간동안 한번만 실행되도록 구현할 수 있다. 쓰로틀링은 로대쉬(Lodash)라이브러리의 쓰로틀(throttle)로 구현하거나 직접 구현할 수 있다. 쓰로틀링 구현은 직접 구현할 경우 setTimeout을 통해 일정 시간동안 스크롤 이벤트를 실행시키고 쓰로틀링을 체크하는 boolean타입의 state를 함께 사용하여 구현할 수 있다. (ex : https://velog.io/@y_jem/%EC%93%B0%EB%A1%9C%ED%8B%80%EB%A7%81throttling%EA%B3%BC-%EB%94%94%EB%B0%94%EC%9A%B4%EC%8B%B1debouncing)

<br>

### # **Lazy Loading은 무엇인가요?**

<br>

- 사용자가 웹 사이트를 접속하게 되면 해당 페이지의 모든 컨텐츠들을 렌더링하게 되는데 이 때 컨텐츠 양이 많은 경우 모든 컨텐츠를 로딩하는 속도가 지연되어 렌더링이 지연될 수 있다. 또한 만약 사용자가 모든 컨텐츠를 보지 않고 나가는 경우 리소스 낭비가 발생할 수 있다. 이럴 때 Lazy Loading 기법을 사용하는데 Lazy Loading 기법은 필요한 리소스를 우선적으로 불러오고 당장 필요하지 않은 리소스들을 추후에 로딩하는 기법을 말한다. Lazy Loading 기법을 통해 렌더링 최적화와 리소스 낭비를 막을 수 있다.

<br>

### # **서버에 트래픽이 주어졌을 때 어떻게 응답속도를 개선할 수 있는가?**

<br>

- 트래픽이란 서버와 스위치 등 네트워크 장치에서 일정 시간 내에 흐르는 데이터의 양을 말한다. 트래픽을 여러 서버로 분산하는 로드 밸런싱이나 분산된 서버에서 데이터를 받아오는 CDN 시스템, 또 요청 데이터의 크기를 줄이기 위한 모듈 번들링, 코드 스플리팅, 레이지 로딩 기법, api 호출 최적화 등을 통해 응답 속도를 개선할 수 있을 것 같다.

<br>

### # **프로젝트를 하면서 메모리 누수(leak) 이슈가 있었는지?**

<br>

- 메모리 누수 이슈가 있었던 적은 없지만 메모리 이슈가 발생한 사례들에 대해 찾아본 적은 있다. useEffect를 사용하여 api 요청 시 api 요청이 늦게 오는 데 컴포넌트가 언마운트 되어 요청이 대기중인 상태, router 이동 후 이동 전 컴포넌트에서 state를 바꾸려는 시도가 있었을 때, 비동기 처리 과정 등 대부분 컴포넌트 언마운트 직전에 특정 작업을 시도했고 특정 작업이 완료되기 전 컴포넌트가 언마운트 되는 경우 메모리 누수가 발생하는 것 같았다. 모두 useEffect의 clean-up 함수로 해결할 수 있었다.

<br>

### # **실제 성능 최적화를 진행한 부분에 대해 설명해달라**

<br>

- 가장 최근에 작업했던 KPA Pedia라는 프로젝트를 기준으로 말씀드리겠다.

  (1) 메모이제이션 값 사용 : useMemo, useCallback hook으로 값, 함수를 메모이제이션하여 사용해 리렌더링을 최소화하였다.

  (2) 캐싱 데이터 사용 : react-query를 사용하여 데이터 캐싱을 통해 api 호출 최적화 작업을 하였다.

  (3) 디바운싱 적용: 검색 기능 중 검색어 입력 시 디바운싱을 적용하여 api 호출 최적화 작업을 하였다.

  (4) 컴포넌트 레이지 로딩 : 라우트를 기반으로 한 컴포넌트 레이지 로딩을 통해 초기 렌더링을 속도를 향상시켰다. (참고 : https://devowen.com/342)

  (5) 모달 사용 : 경고창 사용 시 직접 모달을 만들어서 사용했다. 만약 내장되어 있는 alert, comfirm 등을 사용하게 되면 alert, comfirm은 동기적으로 실행되기 때문에 다음 코드가 실행되지 않을 수 있다. 그렇기 때문에 모달을 직접 만들어서 사용하였다.

<br>

### # **Webpack과 babel**

<br>

- 웹팩

  최신 프론트엔드 프레임워크에서 가장 많이 사용되는 모듈 번들러이다. 모듈 번들러란 웹 애플리케이션을 구성하는 자원(HTML, CSS, Javscript, Images 등)을 모두 각각의 모듈로 보고 이를 압축하고 병합해서 하나의 번들 파일을 만드는 도구를 의미한다.

<br>

- 웹팩 사용 이유

  웹 페이지를 구성하기 위해 HTTP 요청으로 html, css, js, 이미지, 웹 폰트, json 데이터 등 많은 파일을 받아오게 되는데 받아오는 파일이 많을수록 HTTP 요청이 많아지고 주로 사용하는 HTTP 1.1에서는 하나의 커넥션에서 하나의 요청이 끝난 후 다음 요청을 보낼 수 있으므로 HTTP 요청이 많아지면 성능 저하가 발생할 수 있다. 이런 경우 웹팩을 통해 js, css, 이미지 등을 하나로 압축하여 번들 파일을 만들어 파일의 크기를 줄이고 HTTP 요청 횟수를 줄일 수 있다.

<br>

- cra 사용하지 않은 초기 설정 방법

  (0) tsconfig.json에 컴파일 옵션을 설정해준다.

  (1) webpack, webpack-cli, webpack-dev-server, babel-loader, css-loader, file-loader, html-loader, html-webpack-plugin, style-loader, url-loader 등 웹팩 관련 패키지를 설치한다.

  (2) @babel/core, @babel/preset-env, @babel/preset-react, @babel/preset-typescript 등 바벨 관련 패키지를 설치한다.

  (3) 루트 디렉토리 경로에 .babelrc 파일을 만들어준 뒤 presets 속성에 설치한 패키지들을 추가해준다.

  (4) 루트 디렉토리에 webpack.config.js 파일을 생성

  (5) entry 속성에 리액트 파일을 지정하고 output 속성에 웹팩 빌드 후 번들 파일명과 번들 파일의 위치를 지정해준다.

  (6) module 속성 내부에 rules 속성에 각각의 로더들이 컴파일 할 확장자와 제외할 디렉토리를 지정해주고 plugins 속성 내부에 template 속성에 index.html을 지정하여 index.html과 번들 파일을 연결해준다.

  (7) 웹팩 빌드를 위해 package.json 파일 script에 start와 build를 수정해준다.

<br>

- 바벨

  바벨은 ES6+ 버전 이상의 자바스크립트나 JSX, 타입스크립트 코드를 하위 버전의 자바스크립트 코드로 변환 시켜주는 자바스크립트 트랜스파일러이다. 크로스 브라우징 이슈를 해결하기 위해 사용한다. 바벨의 빌드 단계는 파싱(바벨 코어가 수행) -> 변환(플러그인이 수행) -> 출력(바벨 코어가 수행) 단계로 이루어지며 Webpack과 같은 정적 모듈 번들러들을 통해 함께 사용 가능하다.

<br>

- 플러그인

  바벨에 파싱, 변환, 출력 빌드 단계 중 변환 단계를 담당하며 어떤 코드를 어떻게 변환할지에 대한 규칙을 정의한다.

<br>

- 프리셋

  목적에 맞게 여러 가지 플러그인을 세트로 모아놓은 것이다. 제공되는 프리셋으로는 preset-env (최신 문법 ES5로 변환), preset-flow (플로우(타입 체크 라이브러리) 변환), preset-react (리액트 변환), preset-typescript (타입스크립트 변환) 등이 있다.

<br>

- 폴리필

  바벨은 ES6 이후 버전을 ES5 버전으로 변환할 수 있는 코드만 변환한다. 만약 최신 기능을 사용하였는데 이 기능이 ES5 버전에는 존재하지 않아 빌드가 누락 된 부분을 폴리필을 통해 변환할 수 있다. 코어제이에스(corejs), 폴리필아이오(polyfill.io) 등이 대표적인 폴리필 패키지이다.

<br>

### # **prettier, eslint란?**

<br>

- eslint란?

  eslint는 코드 구현 방식을 지정하여 에러를 사전에 방지하고 코드 퀄리티를 보장하도록 도와준다. 또한 코드 스타일과 관련 된 코드 포멧팅도 지원한다.

<br>

- prettier란?

  prettier는 코드 스타일을 통일되도록 도와주는 코드 포멧터이다. eslint와 같이 코드 구현 방식이 아닌, 줄 바꿈, 공백, 들여 쓰기 등 에디터에서 '텍스트'를 일관되게 작성되도록 도와준다.

<br>

- 옵션을 알고 사용하는가?

  모든 옵션에 내용들을 아직 외우지는 못했다. 서칭을 통해 조합하여 사용하고 있다.

<br>

### # 사용자 경험 개선 방법으로 무엇이 있나?

<br>

(1) 스피너 사용 : 페이지 전환이나 api 호출 등 지연 되는 작업의 경우 로딩 중임을 사용자에게 알리는 스피너를 사용한다.

(2) 스켈레톤 UI 사용 : 컨텐츠 로딩 지연 시 사용자의 지루함을 막아주기 위해 로딩 바 혹은 스피너 대신 스켈레톤 UI(대체 UI)를 사용할 수 있다.

(3) 비디오 사용 시 대체 이미지 : 동영상 사용 시 동영상이 보이지 않는 유저들을 위해 대체 이미지를 깔아준다.

(4) 텍스트 드래그 막기 : 드래그 앤 드롭 기능 구현 시 타겟 css에 `use-select: none` 속성을 주어 텍스트가 드래그되는 것을 막을 수 있다.

(5) 이미지 태그의 onError 속성 : api로 이미지를 불러와 띄워줄 경우 이미지를 불러오지 못하는 경우(이미지 주소가 N/A로 오는 경우)가 발생할 수 있는데 이 때 이미지 태그의 onError를 사용하여 대체 이미지를 사용하여 에러 처리를 할 수 있다.

(6) 쿼리 스트링 활용 : 검색 기능 구현 시 쿼리 스트링을 활용하면 사용자가 검색 결과를 다른 사용자들과 공유할 수 있다.

<br>

### # **npm과 yarn은 어떤게 다른가?**

<br>

- 큰 차이는 없지만 yarn은 npm의 개선버전으로 나온 것이며 상대적으로 더 빠르고 보안성이 좋은 것으로 알고 있다. 또한 협업 시에는 같은 패키지 관리자를 사용하는 것이 좋다.

<br>

### # **package.json파일의 역할을?**

<br>

- package.json의 역할

  현재 프로젝트에 관한 정보와 npm, yarn과 같이 패키지 매니저을 통해 설치한 모듈들의 의존성을 관리하는 파일이다.

<br>

- package.json에서 dependencies와 devDependencies의 차이

  개발용과 배포용 라이브러리를 구분해서 설치해야 빌드시간도 줄이고, 배포할 때 불필요한 라이브러리를 포함시키지 않게 된다.

  (1) dependencies : 일반적으로 의존하는 확장 모듈을 관리한다.
  배포 후에도 포함되기 때문에 애플리케이션 동작과 연관된 모듈을 설치한다.
  예를 들어 리액트 돔, 엑시오스, 전역 상태 관리 라이브러리 등이 있다.

  (2) devDependencies : 개발할 때만 의존하는 확장 모듈을 관리한다.
  배포 시 포함되지 않기 때문에 애플리케이션 동작과 직접적인 연관은 없지만, 개발할 때 필요한 라이브러리를 설치하면 된다.
  예를 들어 웹팩, 바벨, 사스, 린트, 테스팅 라이브러리 등이 있다.

<br>

### # **웹 태스크 매니저란?**

<br>

- 웹 태스크 매니저

  개발 업무 시 코드 수정 후 브라우저에서 새로고침을 눌러야 변경된 내용을 볼 수 있으며, 배포 시 HTML, CSS, JS등의 파일을 압축하거나 변환해야 했는데 이러한 과정을 자동화해주는 도구를 웹 태스크 매니저라고 한다. 예를 들어 Grunt(그런트), Gulp(걸프) 등이 있는 것으로 알고 있다. 하지만 그런트와 걸프 같은 경우 웹팩으로 대체하여 사용하는데 완벽히 대체한다기 보다는 웹팩은 모듈 번들러이고 그런트와 걸프는 태스크 러너로 서로 다르지만 웹팩에 그런트와 걸프의 기능이 포함되어 있고 더 많은 기능(Browserify와 같은 의존성 관리 기능)이 포함되어 있기 때문에 웹팩으로 대체하여 사용하는 것으로 알고 있다.

<br>

### # 안티 패턴 알고 있는 것?

<br>

(1) 삼항연산자 : 렌더단에서는 삼항연산자를 사용

(2) map의 key : map 메서드 사용 시 key 값으로 index 사용

(3) 다중 컴포넌트 : 컴포넌트 두 개를 한 파일에 선언

<br>
