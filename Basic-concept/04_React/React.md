## # React

### # SSR / CSR

- SSR / CSR

  - SSR

    서버 사이드 렌더링은 서버에서 HTML 생성해 클라이언트에 전달하는 방식으로 서버에서 그려진 정적인 HTML을 우선 렌더링하고 병렬적으로 Javasciprt 번들 로드가 완료된 후 하이드레이션을 통해 사용자와 상호작용할 수 있도록 하는 방식이다.

  - CSR

    클라이언트 사이드 렌더링은 서버에서 빈 HTML을 전달받아 Javasciprt 번들 로드가 완료되면 동적으로 태그들과 스타일을 생성하여 페이지를 렌더링하는 방식이다.

- SSR / CSR 장단점

  - SSR 장점

    1. 빠른 초기 로딩 : 서버에서 HTML을 렌더링해서 전달하므로, 브라우저가 즉시 화면을 그릴 수 있어 초기 로딩 속도(FCP)가 빠름

    2. SEO 유리 : HTML에 콘텐츠가 포함되어 있어, 검색 엔진 크롤러가 내용을 인식하기 쉬워 검색 노출 최적화에 유리.

  - SSR 단점

    1. 서버 부하 높음 : 새로운 요청 시 서버가 모든 리소스를 준비해서 응답하므로 서버 부하 높고 로딩 속도 늦음

    2. 떨어지는 사용자 경험(UX) : 요청마다 새로고침되며 새 페이지를 받기 때문에, 전통적인 페이지 전환처럼 느껴져 사용자 경험이 떨어질 수 있음. (Next.js는 이를 개선했지만 일반적인 SSR 프레임워크는 여전히 해당 가능성 존재)

    3. TTV와 TTI : HTML을 받아온 후 띄워놓고 JS를 받아오기 때문에 Time To View와 Time To Interaction간에 시간 간격이 존재하여 이벤트 반응 없을 수 있음

  - CSR 장점

    1. 서버 부하 낮음 : 대부분의 로직이 클라이언트에서 처리되므로, 서버는 API 응답만 하면 되어 서버 부담이 적다.

    2. 자연스러운 사용자 경험(UX) : 새로운 요청 시 페이지가 새로고침 되지 않고 클라이언트에서 라우팅을 처리하기 때문에 자연스러운 사용자 경험

  - CSR 단점

    1. 느린 초기 로딩 : 초기에 모든 js 파일을 받아와야 하기 때문에 초기 로딩이 느림, 사용자에게 현재 불필요한 코드나 중복되는 코드 없이 적절한 사이즈의 코드가 적절한 타이밍에 동적으로 로드되도록 하는 code splitting 으로 일부 개선 가능

    2. SEO 불리 : 초기 HTML에는 콘텐츠가 없고 JS 실행 후 렌더링되므로, 검색 엔진이 내용을 수집하기 어려워 SEO에 불리함. react-helmet, react-snap, SSR/SSG 조합 등으로 보완 가능. (다만 구글 봇의 경우 Javascript 해석이 가능, 하지만 해석 실패 가능성이 있고 모든 검색 엔진에 대응하기 어렵기 떄문에 상대적으로 불리한 것은 맞음)

    3. 화면 변하는 모습 노출 : JS가 실행되기 전에는 데이터 없는 뼈대 화면이 보여질 수 있음. 로딩 스피너, 스켈레톤 UI 활용으로 개선 가능.

<br>

- SSR / CSR 동작 순서

  - SSR

    1. 브라우저가 서버에 HTML, CSS, Javascript 파일 등 렌더링에 필요한 리소스 순서대로 요청

    2. 서버에서 HTML, CSS 응답

    3. 브라우저가 HTML/CSS파싱 -> 스타일 -> 레이아웃 -> 페인트 -> 컴포지트 단계를 거쳐 컨텐츠 렌더링

    4. 컨텐츠 렌더링 후 Javascript 파일 요청, Javascript 파일이 로드되면 사용자와 DOM 요소 간 상호 작용 가능

  - CSR

    1. 브라우저가 서버에 HTML 파일 요청

    2. 서버에서 비어있는 HTML 파일 응답

    3. HTML 파일 구성을 위한 Javascript 파일 요청

    4. Javascript 파일 응답 받은 후 동적으로 HTML 파일 구성

    5. 브라우저가 구성 된 HTML 파일을 로드 및 파싱하여 컨텐츠 렌더링

<br>

### # React vs Vue vs Angular

- Libraries, Frameworks 차이

  라이브러리는 흐름을 개발자가 직접 제어한다. 필요한 기능이 있을 때 라이브러리를 가져다 사용하는 것이다. 반대로 프레임워크는 프레임워크가 흐름을 가지고 있다. 프레임워크가 짜 놓은 틀에서 코드를 작성하게 된다.

- Libraries, Frameworks 사용하는 이유

  규모가 커지고 복잡한 애플리케이션을 개발하며 생산성을 향상시키고 많은 양의 데이터 관리와 코드 유지 보수를 더욱 편리하게 하기 위해 다양한 Frontend Framework,Library가 등장하고 사용하게 되었다.

- React(라이브러리), Vue(프레임워크), Angular(프레임워크) 중 React를 사용하는 이유

  처음 프레임워크, 라이브러리 사용하여 개발을 시작하게 되었을 때 React, Vue, Angular 중 React를 선택한 이유는 더 큰 개발 생태계를 가지고 있기 때문이었습니다. 현재도 npm 패키지 다운로드 수를 비교해보면 React 패키지 다운로드 수가 압도적입니다. 또한 React나 Vue 모두 오픈 소스이고 정기적으로 버전을 릴리즈하고 있지만 개인이 기업에 후원을 받아 관리되는 Vue Facebook이 직접적으로 관리하는 React가 지속적으로 신뢰할 수 있는 라이브러리라고 생각했습니다.

<br>

### # React란

- 특징

  1. 가상 돔(Virtual DOM) : 가상 돔은 실제 DOM에 적용시키기 전 가상 DOM에 변화된 부분을 먼저 적용시킨 후 변화된 부분만 렌더링 되도록 하여 최소한의 연산을 통해 성능을 증가시킨다.

  2. 단방향 데이터 바인딩 : 데이터가 부모 → 자식 방향으로만 흐르는 단방향 데이터 바인딩 구조를 갖고 있어, 데이터의 추적이 용이하고 애플리케이션 상태를 예측하기 쉬운 장점이 있다. 거꾸로 부모의 데이터를 바꿔주기 위해서는 state를 이용해야 한다.

  3. JSX 문법과 선언형 프로그래밍 : HTML과 JavaScript를 결합한 JSX(JavaScript XML) 문법을 통해 선언적으로 프로그래밍한다. 코드의 흐름보다 결과에 집중함으로써 코드 의도 파악이 쉽다.

  - JSX : JSX는 Javascript에 XML을 추가하여 확장한 문법이다. 공식적인 자바스크립트 문법은 아니며 브라우저에서 실행하기 전 번들링 과정 중 바벨을 사용하여 일반 자바스크립트로 변환된다.

  4. 컴포넌트 기반 UI 구성 : 재사용이 가능한 개별적인 모듈인 컴포넌트를 통해 UI를 구성한다.

- 장단점

  - 장점

    1. 컴포넌트 기반 아키텍처 : UI를 독립적인 컴포넌트 단위로 구성하여 재사용성과 유지보수성이 높다.

    2. 가상 돔을 통한 성능 최적화 : 상태가 변경되면 가상 돔과 실제 돔을 비교하여 변경된 부분만 실제 DOM에 반영함으로써 불필요한 DOM의 조작을 줄여 렌더링 성능이 향상

    3. 넓은 생태계 : Vue나 Angular에 비해 사용자가 압도적으로 많고 커뮤니티나 자료가 방대, 문제 해결이나 확장 개발 시 유리

  - 단점

    1. 내장 기능 부족 : View 계층만 담당하므로 라우팅, 상태관리 등은 직접 구현하거나 React Router, Redux 같은 써드파티 라이브러리를 사용해야 하는 번거로움이 있다.

    2. CSR 기반의 한계 : CSR 기반이기 때문에 초기 렌더링 성능, SEO 문제 등이 있을 수 있다. SSR이 가능하기는 하지만 별도의 설정이 필요하다.

<br>

### # React Lifecycle Methods

- 리액트 라이프사이클 순서

  생성(mount) -> 갱신(update) -> 제거(unmount)

- 각 메소드들을 언제 사용하는지?

  (1) componentDidMount : 컴포넌트가 생성된 직 후 호출

  (2) shouldComponentUpdate : props 또는 state가 새로운 값으로 갱신되어 렌더링이 발생하기 직전에 호출

  (3) componentDidUpdate : 리렌더링 완료 후 호출

  (4) componentWillUnmount : 컴포넌트가 화면에서 사라지기 직전에 호출

  (5) componentDidCatch : render 함수 에러 발생 시 호출

- 라이프사이클 중 써본 메소드가 뭐가 있는지?

  클래스형으로 작업하지 않기 때문에 라이프사이클 메소드는 사용해본 적이 없다. 대신 생명주기 메서드를 대체할 수 있는 useEffect hook을 자주 사용하였다. useEffect에 의존성 배열로 빈 대괄호를 사용하면 componentDidMount의 역할을 하고, 함수를 return하면 componentWillUnmount 역할을 한다. 또한 의존성 배열을 아예 사용하지 않거나, 의존성 배열에 값을 넣어 componentDidUpdate를 대체할 수 있다.

- componentDidMount 와 render 중 무엇이 먼저 실행되는지?

  componentDidMount 메서드보다 render 메서드가 먼저 실행되는 것으로 알고 있다.

<br>

### # javascript로 useState 구현

```javascript
let states = [];
let currentIndex = 0;

function useState(initialValue) {
  const index = currentIndex;

  if (states[index] === undefined) {
    states[index] = initialValue;
  }

  function setState(newValue) {
    states[index] = newValue;
    render(); // 상태 변경 시 리렌더링 트리거 (가상의 함수)
  }

  currentIndex++;
  return [states[index], setState];
}

function render() {
  currentIndex = 0;
  App(); // 다시 컴포넌트 렌더링
}
```

<br>

### # useEffect hook

- 설명

  useEffect는 클래스형 컴포넌트의 생명주기 메소드를 대체하기 위해 사용한다. 컴포넌트 마운트(컴포넌트가 화면에 그려짐, 즉 렌더링 과정 중 페인트까지 완료), 컴포넌트 언마운트(컴포넌트가 화면에서 사라짐), 의존성 배열 값 변경 시 실행할 수 있다.

- 실행 예시

  - 의존성배열 값 x, return 함수 x : 내부 로직이 컴포넌트 마운트 시 실행

    ```javascript
    useEffect(() => {
      ...
    }, []);
    ```

  - 의존성배열 값 o, return 함수 x : 내부 로직이 컴포넌트 마운트 시 실행, 의존성 배열 값 변경 시 실행

    ```javascript
    useEffect(() => {
      ...
    }, [abc]);
    ```

  - 의존성배열 값 x, return 함수 o : 내부 로직이 컴포넌트 마운트 시 실행, return 함수는 컴포넌트 언마운트 시 실행

    ```javascript
    useEffect(() => {
      ...

      return () => {...};
    }, []);
    ```

  - 의존성배열 값 o, return 함수 o : 내부 로직이 컴포넌트 마운트 시 실행, 의존성 배열 값 변경 시 실행, return 함수는 컴포넌트 언마운트 시 실행, 의존성 값 변경 직전에 이전 이펙트 정리를 위해 실행 (이전 이펙트 정리란, 리렌더링 후 useEffect 본문을 실행하는 것이 아닌 clean up 먼저 실행 후 본문을 실행함)

    ```javascript
    useEffect(() => {
      ...

      return () => {...};
    }, []);
    ```

    ```javascript
    // 예시
    import { useEffect, useState } from "react";

    function App() {
      const [count, setCount] = useState(0);

      useEffect(() => {
        console.log("🟢 effect 실행:", count);

        return () => {
          console.log("🔴 cleanup 실행:", count);
        };
      }, [count]);

      return (
        <div>
          <p>{count}</p>
          <button onClick={() => setCount((c) => c + 1)}>증가</button>
        </div>
      );
    }

    // effect 실행: 0      ← 최초 마운트
    // cleanup 실행: 0     ← count = 1로 변경되어 리렌더링된 후
    // effect 실행: 1      ← 새로운 값 기준으로 effect 실행
    // 결론 : 리렌더링 → 화면 반영 → 그 이후에 cleanup → 본문 실행
    ```

  - 의존성배열 x : 컴포넌트 리렌더링마다 실행

    ```javascript
    useEffect(() => {
      ...
    });
    ```

<br>

### # 가상 돔(Virtual DOM)

웹에서 DOM 조작은 비용이 크고 성능 저하를 일으키기 쉽다. 왜냐하면 DOM 노드 하나가 변경되면, 브라우저는 리플로우와 리페인트 단계를 다시 거치는 리렌더링이 발생한다. 리렌더링은 연산 비용이 크기 때문에 잦게 발생하는 경우 성능 저하를 유발하게 된다.

특히 SPA(싱글 페이지 애플리케이션)는 CSR(클라이언트 사이드 렌더링) 방식을 채택하여 사용하는데 CSR은 javascript로 HTML을 생성하며 잦은 돔의 변화가 일어난다는 특징이 있다. 그런데 DOM에 변화가 일어날 때마다 리렌더링 과정을 반복하게 되면 많은 연산 비용이 발생하게 되므로 성능 이슈가 발생할 수가 있다.

react는 이 문제를 해결하기 위해 가상 돔을 사용한다. 가상 돔은 이전 가상 돔의 상태를 메모리에 저장해놓고 메모리 상에서 이전 가상 돔(변경 전)과 새로운 가상 돔(변경 후)의 상태를 비교한 뒤 최소한의 내용만 실제 DOM에 반영 하는 프로그래밍 개념이다.

가상 돔은 실제 렌더링하는 것이 아닌 메모리 상에서 동작하기 때문에 훨씬 빠르고 여러 번에 상태 변화 시 배치처리를 통해 한번에 실제 돔에 반영시키므로 리렌더링 횟수를 최소화하여 성능을 크게 향상시켰다.

<br>

### # Props / State

- Props

  상위 컴포넌트가 하위 컴포넌트에 전달하는 데이터를 가진 객체이다. 단방향 데이터 흐름을 가지며 자식 입장에서는 직접 수정할 수 없다는 특징이 있다. 변수, state, 함수 등 모두 전달할 수 있다.

- State

  컴포넌트 내부에서 가지고 있는 컴포넌트의 상태값이다. 유동적인 데이터를 다루기 위한 객체이다.

- let으로 변수 선언해서 관리하면 될껄 왜 state로 관리할까?

  state는 일반 변수와 다르다. setState를 통해 값이 변하게 되면 render 함수를 호출하여 자동으로 리렌더링이 발생한다. 값이 변함에 따라 컴포넌트를 최신으로 유지해야 하기 때문에 render 함수를 호출하는 state를 사용하는 것이다. let과 같은 일반 변수는 값이 변경되어도 자동으로 리렌더링이 발생하지 않는다.

- Props vs State

  1. props는 자식 컴포넌트로 전달되고 state는 컴포넌트가 직접 관리한다.

  2. props는 직접 변경할 수 없고 state는 직접 변경이 가능하다.

- 왜 state를 직접 변경하지 않고 setState를 이용하나요?

  컴포넌트는 현재의 state와 setState를 얕은 비교(참조 비교)해서 setState의 참조가 바뀌게 되면 업데이트 됬다고 감지하게 되어 render 함수를 호출하는데, state를 직접 setState의 참조가 바뀌지 않아 render 함수를 호출하지 않게 되어 상태 변경이 일어나도 리렌더링이 일어나지 않는다. 즉 불변성이 지켜지지 않는 경우 리렌더링이 발생하지 않는다. 상태 변경을 추적하고 변경에 따라 구성 요소의 최신화를 유지하기 위해서는 반드시 setState를 사용해야 한다. (추가 내용 : setState를 통해 root.render 함수 호출 시 리렌더링이 되는 이유는 컴포넌트 return 함수 내부에서 최신 state 값이 포함된 React.createElement 함수를 호출하여 새로운 react element를 생성하는데 이 element들을 렌더링하는 것이 render 함수이다. 그렇기 때문에 state 값 변경 시 setState를 사용하여 render 함수가 정상적으로 호출되게 해야한다.)

- 객체, 배열 setState 시 spread 문법 사용 이유

  불변성은 변하지 않는 상태나 값을 말한다. 리액트에서의 불변성은 값을 직접적으로 변경을 하지 않고, 기존의 값을 수정하지 않으면서 새로운 값을 만들어내는 것을 의미한다. 원시 타입의 경우 값이 변경되는 경우 기존 값을 직접 변경하는 것이 아닌 콜스택에 새로운 메모리를 생성하여 새로운 메모리를 참조하도록 동작한다. 즉 불변성을 가지고 있다. 하지만 객체 타입의 경우 값이 변경되는 경우 메모리힙에 새로운 메모리를 생성하지않고 값을 직접 변경하도록 동작한다. 리액트에서는 이러한 객체 타입의 불변성을 지켜주고자 spread 문법을 사용했다. 리액트는 얕은 비교를 통해 state의 업데이트를 감지한다. 얕은 비교는 실제 내부 값까지 비교하는 것이 아닌 참조하는 값에 메모리 주소를 비교하는 것이다. 기존 값과 최신 값에 얕은 비교를 수행하여 최신 값이 새로운 메모리 주소를 참조할 때 업데이트가 발생하게 되는 것이다. 이 때 배열이나 객체의 상태를 업데이트 하는 경우 리액트에서는 새로운 메모리 주소를 생성하기 위해 setState에 배열이나 객체를 할당하고 배열이나 객체 내부에 스프레드 연산자를 활용한 기존 값의 복사본과 최신 값을 할당해준다. 이렇게 복사본을 활용한 방식과 새로운 메모리 주소를 생성하는 방식을 통해 불변성을 지킬 수 있고 불변성을 지켜줌으로서 예상치 못한 사이드 이펙트를 방지할 수 있고 얕은 비교를 통해 효과적인 상태 업데이트를 할 수 있다. 만약 불변성을 지키지 않고 기존 값을 직접 변경할 경우 참조하는 값에 메모리 주소가 동일하기 때문에 리액트는 상태 변화를 감지할 수 없어 컴포넌트의 최신화를 유지할 수 없게 된다. 이 때 setState의 동작 방식을 확인해보면 만약 setState로 이전 값과 동일한 값으로 업데이트한다고 했을 때 원시 타입의 경우 동일한 값이면 리렌더링이 발생하지 않고 객체 타입의 경우 동일한 값이라도 리렌더링이 발생하게 된다. 이유는 위와 같이 객체 타입의 경우 내부 값은 상관하지 않고 spread 문법을 통해 새로운 메모리 주소를 가진 데이터를 항상 만들어내기 때문에 이전 state와 최신 state 얕은 비교 시 참조 주소가 변경되었기 때문에 계속해서 리렌더링이 발생하는 것이다. 하지만 원시 타입의 경우 같은 값으로 업데이트되는 경우 이전 state와 최신 state는 여전히 동일한 메모리를 가리키고 있기 때문에 리렌더링이 발생하지 않는다.

  ```javascript
  const [user, setUser] = useState({ name: "Kim" });

  // 에러 케이스
  user.name = "Lee"; // 원본 직접 수정
  setUser(user); // 참조값은 그대로 → 리렌더링 x

  // 정상 케이스
  setUser({ ...user, name: "Lee" }); // 새로운 객체 생성 → 리렌더링 발생
  ```

- useState를 컴포넌트 최상위에서 사용하는 이유와 react hook을 조건문 등으로 감쌀 수 없는 이유

  React는 내부적으로 컴포넌트를 렌더링할 때 훅을 순서대로 호출하며 상태를 저장한다.

  ```jsx
  // 정상 예시
  function MyComponent() {
    const [count, setCount] = useState(0); // 첫 번째 훅
    const [name, setName] = useState(""); // 두 번째 훅

    return (
      <div>
        {count} {name}
      </div>
    );
  }

  // React는 이 컴포넌트를 렌더링하면서 이렇게 기억한다.
  // - 1번째 useState → count 상태
  // - 2번째 useState → name 상태
  ```

  즉, React는 훅이 어떤 변수에 들어가는지 이름은 기억 하지 않고 몇 번째 훅인지만 기억한다. 그렇기 때문에 아래와 같이 조건문 안에서 훅을 쓰게 되면 상황에 따라 count 훅이 호출되기도 하고 안 되기도 하기 때문에 React에서 name 훅을 다른 count로 인식하거나 아예 상태가 꼬여서 버그가 생기게 되는 것이다. 즉 훅의 호출 순서가 바뀌면 React가 상태를 잘못 연결하게 된다.

  ```jsx
  // 에러 예시
  function MyComponent() {
    if (someCondition) {
      const [count, setCount] = useState(0); // ❌ 조건문 안
    }
    const [name, setName] = useState("");
  }

  // 첫 번째 렌더링 (someCondition 조건 참) : 상태 1 -> count, 상태 2 -> name
  // 두 번째 렌더링 (someCondition 조건 거짓) : 상태 1 -> 없음, 상태 2 -> name
  ```

  그렇기 때문에 항상 컴포넌트 최상위에서 실행하여 useState 훅의 순서를 보장해야한다. 훅의 호출 순서를 고정시키기 위해서이다. 만약 조건에 따라 상태를 다르게 만들고 싶으면 아래와 같이 초기화할 수 있다. 아래와 같이 하면 훅의 순서는 유지되면서도 조건에 따라 상태를 다르게 설정할 수 있다. (useState에 콜백 함수를 넘기면, 컴포넌트가 처음 렌더링될 때 한 번만 실행된다.)

  ```jsx
  function MyComponent({ isLoggedIn }) {
    const [user, setUser] = useState(() => {
      if (isLoggedIn) {
        return { name: "홍길동" };
      } else {
        return null;
      }
    });

    return <div>{user ? user.name : "로그인 필요"}</div>;
  }
  ```

  useEffect, useRef 같은 다른 훅도 똑같은 규칙이 적용된다.

<br>

### # react batch update

setState는 비동기로 동작한다. 비동기로 동작하는 이유는 일정 시간동안 변화하는 상태를 모아 한번에 렌더링하기 위해서이다. 이러한 업데이트 방식을 배치 업데이트라고 한다. 리액트의 배치 업데이트(batch update)는 16ms(밀리세컨드)당 한번만 일어난다. 만약 배치 업데이트를 하지 않는다면 setState를 100번 연속 호출했을 때 100번의 리렌더링이 발생하여 성능 저하가 발생할 수 있다. 그러므로 react는 배치 업데이트를 사용하여 16ms마다 업데이트 된 state를 한번에 처리하여 리렌더링의 횟수를 줄여 성능을 향상시켰다. 하지만 배치 업데이트로 인해 state 업데이트 후 바로 state 값을 참조하여 다른 작업을 할 때 문제가 발생할 수 있다. 이런 경우 이전 state를 바로 참조할 수 있는 prevState를 활용하여 상태를 동기적으로 업데이트 한 후 사용하는 방식으로 해결 할 수 있다. prevState는 setState 인자로 함수를 전달하고 해당 함수의 파라미터로 이 전 state를 전달하는 방식으로 사용할 수 있다. (ex : `setState((prev) => prev + 1`)

<br>

### # react 렌더링 과정

1. Render Phase (렌더링 단계) -> 가상 DOM 생성 + 변경 감지 (Diffing + Reconciliation)

   Babel이 JSX를 react element 객체를 반환하는 React.createElement()로 변환하고

   ```jsx
   // 트랜스파일링 전
   const element = <h1>Hello</h1>;

   // 트랜스파일링 후
   // 결과는 순수 JavaScript 객체입니다 (React 엘리먼트 객체).
   const element = React.createElement("h1", null, "Hello");
   ```

   이후 ReactDOM.createRoot(container).render(element) 호출 시, React는 이 react 엘리먼트를 기반으로 내부적으로 새로운 Fiber Tree를 구성한다.

   ```jsx
   const root = ReactDOM.createRoot(document.getElementById("root"));
   root.render(<App />);
   ```

   그 후 이전 렌더링의 Fiber Tree와 비교(Diffing)하고 비교 결과를 기반으로 어떤 노드는 재사용, 삭제, 새로 생성할 지 재조정(Reconciliation)을 통해 판단한 뒤 최종 변경 사항을 메모리에 저장한다. 이때 실제 DOM은 절대 건드리지 않는다.

2. Commit Phase (커밋 단계) – 실제 DOM 업데이트 수행

   Render Phase에서 수집된 변경 사항(EffectList)을 기반으로 실제 DOM 트리에 컴포넌트를 마운트한다. 즉 실제 DOM 트리에 변경된 내용을 삽입하여 브라우저 HTML 요소로 표시하는 것이다. (컴포넌트 마운트 : 컴포넌트가 처음 렌더링되어 브라우저의 DOM에 추가되는 시점을 말한다.) 이 때 페인팅 단계 전 useLayoutEffect, 페인팅 단계 후 useEffect 등이 처리된다.

3. 화면에 실제 반영 (최종 렌더링)

   변경된 부분만 효율적으로 반영되어, 불필요한 DOM 조작이 줄어든다. 이후 이벤트 바인딩, useEffect, 애니메이션 등 후처리가 이뤄진다.

<br>

### # react 리렌더링 조건

- 기본 리렌더링 조건

  1. 부모 컴포넌트가 렌더링 될 때

  2. 자신의 state가 변경 될 때

  3. 자신이 전달받은 props가 변경될 때

- React에서 리렌더링을 막아야하는 경우

  무분별하게 막아야하기 보다는 필요한 상황에 막아야한다. 가상 돔을 사용하여 컴포넌트를 업데이트시키는데 이유없이 리렌더링을 막으려고 한다면 큰 이점없이 코드만 더 복잡해질 수 있다.

  - 사용자 입력값 유지 : 예: input에 사용자가 입력하는 중인데, 리렌더링으로 커서가 튀거나 값이 초기화됨.

  - 불필요한 API 호출 유발 : 리렌더링 될 때마다 useEffect 등으로 의도치 않은 네트워크 요청이 발생.

  - 무의미한 렌더링 반복 : 예: prop이 객체이고 참조값은 변했지만 내용은 동일 → 얕은 비교로 자식이 매번 리렌더링됨.

  - 비싼 연산을 포함한 컴포넌트 : 복잡한 차트, 대용량 리스트 등 렌더링 비용이 높은 컴포넌트가 자주 리렌더링되면 성능 저하 발생.

- React.createElement이란?

  - react는 `jsx 문법`을 사용하고 있다. jsx 문법은 js에 XML을 추가하여 확장한 문법이다. 브라우저에서 실행하기 전 번들링 과정 중 바벨을 사용하여 일반 자바스크립트로 변환되는데 이 자바스크립트 내부에서 `React.createElement` 를 호출하는데 `createElement` 는 react 엘리먼트를 생성하기 위한 정보를 담은 객체를 반환한다. createElement는 type, props, children 순으로 인자를 받아 react 엘리먼트를 생성한다.

    ```jsx
    // type : MyLabel(컴포넌트 이름), div(태그이름), input(태그이름)
    // props : 아래 예시에서는 객체 형태로 전달받고 있음
    // children : 아래 예시에서는 react 엘리먼트를 children으로 받고 있음
    return React.createElement(
      MyLabel,
      { label: "Here is the label prop" },
      React.createElement(
        "div",
        {},
        React.createElement("input", {
          type: "text",
          value: "And here is a child",
        })
      )
    );
    ```

  - reateElement를 통해 생성 된 엘리먼트 객체를 함수 컴포넌트의 return 문 내부에 배치(클래스형 컴포넌트의 경우 render 함수에 인자로 주어졌을 경우)하면 렌더링 과정에서 React DOM을 React 엘리먼트 객체와 일치하도록 DOM을 업데이트하여 화면에 그려주게 된다.

  - 화면에 그려지기 전 createElement 통해 생성한 엘리먼트는 정보를 담고 있는 `객체(object)`일 뿐이다. return 문 내부에 배치되어 렌더링 되기 전까지 어떤 것도 실행할 수 없는 단지 정보의 집합체인 것이다.

  - react 엘리먼트는 불변(immutable)하다. 즉 생성 후에는 엘리먼트의 자식, 속성 등을 변경할 수 없는 상수다. 따라서 엘리먼트 내용이 변경된다는 것은 createElement를 통해 변경(혹은 변경되지 않은)된 정보를 담아 `새로운 객체(object)를 생성`한다는 것을 의미한다.

- children과 렌더링

  - children이란?

    `children`은 커스텀 컴포넌트 태그 사이에 삽입되는 태그들을 컴포넌트 내부 props로 받아서 사용하는 객체를 말한다. 이 객체는 react element 객체이다. 대체로 모달이나 바텀시트와 같은 공통 컴포넌트를 만들 때 사용하거나 렌더링 최적화를 위해 사용한다.

  - children을 사용하는 컴포넌트에서 리렌더링 발생 시 children은 리렌더링 하지 않는 이유

    자식 컴포넌트를 사용할 때 `<Component />` 와 같이 컴포넌트 형태로 사용할 때는 리렌더링 발생 시 자식 컴포넌트의 `createElement` 가 새로 호출되어 자식 컴포넌트도 함께 리렌더링 되는 것이고 children 형태로 사용할 때는 새로 `createElement` 를 호출하는 것이 아닌 전달 받을 때 이미 호출 된 `createElement` 결과 값인 react 엘리먼트 객체를 전달받아 사용하기 때문에 자식 컴포넌트는 리렌더링이 발생하지 않는다.

  - children은 언제 사용하는 것이 좋을까?

    1. 부모 컴포넌트를 감싸고 있는 컨테이너가 빈번하게 렌더링 되지 않는 조건일 때 사용한다. 왜냐하면 이와 같은 환경에서 자식 컴포넌트를 children으로 받아오게 되면 컨테이너가 리렌더링 될 때 마다 부모 컴포넌트는 불가피하게 함께 리렌더링 되기 때문이다. 이런 경우 부모 컴포넌트 내부에서 자식 컴포넌트를 그대로 사용하고 부모 컴포넌트를 React.memo로 감싸 최적화할 수 있다.

    2. 반복적으로 쓰이는 디자인 레이아웃을 제작할 때 사용한다. 코드 재사용성을 극대화하여 생산성과 가독성을 증가시킬 수 있다.

- React.memo

  - React.memo란?

    React.memo는 props가 바뀌지 않으면 컴포넌트를 리렌더링하지 않도록 막는 고차 컴포넌트이다. 내부적으로 얕은 비교(shallow comparison)를 사용해서 props를 비교한다. 단 매번 변하는 props를 받아오는 컴포넌트나 레퍼런스가 계속 변하는 콜백 함수를 props로 받는 컴포넌트의 경우 React.memo를 사용하면 오히려 성능 저하가 올 수 있으므로 성능 향상의 이점이 있을 때에만 사용하는 것이 좋다.

  - children props를 전달 받는 컴포넌트에서 React.memo가 동작하지 않는 이유

    우선 React.memo는 참조 주소만 비교하는 얕은 비교를 통해 메모이징 된 컴포넌트를 사용할 지 결정하는데 children props를 사용하는 컴포넌트 내부에서 React.memo가 동작하지 않는다는 것은 props로 전달 받는 children의 참조 주소가 변경되었다는 것을 의미한다. 내부 children의 참조 주소가 변경되었기 때문에 메모이징한 컴포넌트를 사용하지 않는 것이다.

    children props를 자식 컴포넌트로 전달하는 부모 컴포넌트가 리렌더링 될 때 children props에 해당하는 컴포넌트의 createElement가 새로 호출된다. 부모 컴포넌트 내부에서 createElement가 새로 호출 되면 새로운 react 엘리먼트 객체를 리턴하게 되고 해당 객체를 다시 자식 컴포넌트의 children props로 전달하게 된다. 이렇게 되면 이전에 전달했던 react 엘리먼트 객체와 리렌더링 후 새롭게 생성 된 react 엘리먼트 객체의 참조는 다르게 되어 children을 사용하고 있는 자식 컴포넌트 내부에서는 React.memo가 동작하지 않게 된다.

<br>

### # 컴포넌트

- 컴포넌트에 대해 설명해달라

  재사용이 가능한 UI 구성 단위이다. 컴포넌트는 재사용이 가능하고, 개별로 관리되기 때문에 유지 보수에 좋고 렌더단(render 함수 내)에서 페이지 구성을 파악하기 편하다.

- 컴포넌트를 나누는 기준

  1. 페이지를 구성하는 요소 (nav, footer 등)

  2. 재사용이 필요한 반복되는 요소인 경우

  3. 한 컴포넌트 내에 코드 길이가 길어 가독성이 떨어지는 경우

### # Hooks

- Hooks

  공식 문서에서는 Hook은 함수 컴포넌트에서 React state와 생명주기 기능을 연동할 수 있게 해주는 함수라고 한다. react를 클래스 없이 사용할 수 있게 해준다. 클래스형 컴포넌트의 단점을 보완하기 위해 만들어졌다. 최상위 레벨에서 호출해야하며 함수 컴포넌트 내에서 호출해야한다.

- Hooks가 만들어진 이유는?

  클래스형 컴포넌트에

  1. extends와 super(props)를 매번 작성

  2. 함수, props 등 사용 시 매번 this에 bind 후 사용

  3. 고차 컴포넌트 지옥

  와 같은 문제로 인해 Hooks가 만들어지게 되었다.

- Hooks를 어떻게 사용했는지?

  useState, useEffect, useNavigate, useCallback, useMemo, useRef, useQuery, useInview, custom hook 등을 사용하였다.

- 클래스형 컴포넌트와 함수형 컴포넌트의 차이

  1. 선언 방식 (클래스 class로 시작하고 컴포넌트로 상속, 함수 일반 함수 생성과 동일)

  2. lifeCycle 관련 기능 사용 여부 (클래스 O, 함수 X)

  3. 메모리 자원 사용량 (클래스 > 함수)

  4. state, props 사용 방법 (클래스 this로 사용, 함수 this없이 사용)

<br>

### # 리덕스(Redux)

- 리덕스란

  리덕스 디자인 패턴은 FLUX 패턴이다. MVC 패턴의 단점으로 FLUX 패턴이 생겨났는데 MVC 패턴은 양방향 데이터 흐름을 가지고 있어 프로젝트 규모가 커지게 되면 구조가 매우 복잡해지고 예측 불가능한 결과를 나타낼 수 있다. 그래서 생겨난 것이 단방향 데이터 흐름을 가지고 있는 FLUX 패턴이다. FLUX 패턴의 데이터 흐름은 항상 Dispatcher -> Store -> View -> Action을 통해 다시 -> Dispatcher로 데이터가 흐르게 된다. 단방향 데이터 흐름의 장점은 데이터 변화에 따른 성능 저하 없이 DOM 객체 갱신이 가능하고 데이터 흐름이 단방향이기 때문에 코드를 이해하기 쉽고 데이터 추적과 디버깅이 쉽다. 단점은 변화를 감지하고 화면을 업데이트하는 코드를 매번 작성해야 한다는 단점이 있다.

- 리덕스 사용법 (https://ivorycode.tistory.com/entry/Redux%EC%9D%98-%ED%9D%90%EB%A6%84%EA%B3%BC-%EC%98%88%EC%A0%9C, https://devlog-h.tistory.com/14)

  1. 액션 생성 : 액션은 state의 액션을 정의한다. 리듀서는 이 액션을 참고하여 state를 어떻게 변화시킬 지 결정하게 된다.

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

  2. 리듀서 생성 : 리듀서는 액션의 결과를 보고 state를 업데이트시켜 반환한다.

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

  3. 컴바인리듀서 생성 : 컴바인리듀서는 모든 리듀서를 하나로 합쳐준다.

     컴바인 리듀서 생성을 위해 필요한 컴바인리듀서 함수, 생성해놓은 리듀서 함수를 임포트한다.
     그 후 컴바인리듀서 함수에 인자로 리듀서 함수를 객체로 전달하고 스토어 생성 시 사용해야하므로 익스포트하여 내보낸다.

     ```js
     export default combineReducers({
       // 리듀서 이름: import한 리듀서
       counterData: counter,
     });
     ```

  4. 스토어 생성 : 스토어는 state가 저장되는 저장소이다.

     스토어가 가지고 있는 state를 전체 컴포넌트에서 공유하기 위해서 최상위 컴포넌트에 스토어를 연결해야한다.
     스토어 연결을 위해 필요한 크리에이터스토어 함수, 프로바이더 컴포넌트, 컴바인리듀서 함수(네이밍은 rootReducer를 많이 사용)를 임포트한다. 그 후 store 변수를 생성하여 크리에이터스토어 함수를 할당하는데 인자로 컴바인리듀서 함수를 전달하고
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

  5. 디스패처 생성 : 디스패치는 리듀서에 액션을 전달한다.

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

  6. 셀렉터 생성 : 셀렉터는 스토어에 state를 가져온다.

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

- 리덕스 미들웨어란

  리덕스 미들웨어는 액션이 디스패치(dispatch) 된 후 리듀서가 해당 액션을 처리하기 전에 추가 작업(로깅, 비동기 처리, 에러 처리 등) 을 할 수 있도록 해주는 함수이다.
  Redux는 기본적으로 순수 함수인 리듀서를 기반으로 하기 때문에, 리듀서 안에서 직접 API 요청이나 타이머 같은 부수효과(side effect)를 처리할 수 없다.
  즉, dispatch(fetchUser())와 같은 액션을 날렸을 때 내부에서 비동기 로직을 처리해 상태를 변경하려면 미들웨어가 필요하다.
  미들웨어는 기본적으로 디스패치 함수를 감싸서 확장하는 고차 함수(Higher-Order Function) 형태로 작동하며, 이를 통해 액션을 가로채거나 변형하거나 비동기 작업을 처리할 수 있다.
  대표적인 리덕스 미들웨어 라이브러리로는 redux-thunk, redux-saga, redux-observable, redux-promise-middleware 등이 있습니다.

- redux-thunk

  - 개념

    redux-thunk는 액션 크리에이터가 객체가 아닌 함수를 반환할 수 있게 해주는 미들웨어이다. 이 함수는 dispatch, getState를 인자로 받아, 내부에서 비동기 작업을 처리하고,
    필요에 따라 여러 개의 액션을 순차적으로 dispatch할 수 있게 해준다.

  - 예시

    dispatch -> 액션을 디스패치할 수 있는 함수, getState -> 현재 Redux 상태 트리를 가져오는 함수(const state = getState())

    ```js
    // 썽크 액션 크리에이터 (비동기 처리)

    const fetchUser = (userId) => {
      return async (dispatch, getState) => {
        dispatch({ type: "FETCH_USER_REQUEST" }); // 1단계: 로딩 시작

        try {
          const res = await fetch(`/api/user/${userId}`); // 2단계: 비동기 API 호출
          const data = await res.json(); // 3단계: 응답 파싱
          dispatch({ type: "FETCH_USER_SUCCESS", payload: data }); // 4단계: 성공 액션
        } catch (err) {
          dispatch({ type: "FETCH_USER_FAILURE", error: err }); // 5단계: 실패 액션
        }
      };
    };

    store.dispatch(fetchUser(1)); // thunk 함수를 dispatch
    ```

- redux-saga

  - 개념

    redux-saga는 비동기 로직을 제너레이터 함수(generator function)를 사용해서 처리한다. 액션을 감지해서(take, takeLatest 등) 특정 사가(generator 함수)가 실행되고,
    그 안에서 call, put, delay 같은 이펙트 유틸을 사용해 명령형으로 비동기 로직을 다룬다.

  - 예시

    1. 버튼 클릭 → FETCH_USER_REQUEST 액션 디스패치

    2. 사가가 감지 → API 호출

    3. 성공하면 FETCH_USER_SUCCESS → 리듀서가 상태 업데이트 → 화면에 표시

    ```js
    // actions.js
    // 액션 타입
    export const FETCH_USER_REQUEST = "FETCH_USER_REQUEST";
    export const FETCH_USER_SUCCESS = "FETCH_USER_SUCCESS";
    export const FETCH_USER_FAILURE = "FETCH_USER_FAILURE";

    // 액션 생성자
    export const fetchUserRequest = (userId) => ({
      type: FETCH_USER_REQUEST,
      payload: userId,
    });

    export const fetchUserSuccess = (user) => ({
      type: FETCH_USER_SUCCESS,
      payload: user,
    });

    export const fetchUserFailure = (error) => ({
      type: FETCH_USER_FAILURE,
      error,
    });
    ```

    ```js
    // reducers.js
    import {
      FETCH_USER_REQUEST,
      FETCH_USER_SUCCESS,
      FETCH_USER_FAILURE,
    } from "./actions";

    const initialState = {
      loading: false,
      data: null,
      error: null,
    };

    export const userReducer = (state = initialState, action) => {
      switch (action.type) {
        case FETCH_USER_REQUEST:
          return { ...state, loading: true, error: null };
        case FETCH_USER_SUCCESS:
          return { ...state, loading: false, data: action.payload };
        case FETCH_USER_FAILURE:
          return { ...state, loading: false, error: action.error };
        default:
          return state;
      }
    };
    ```

    ```js
    // sagas.js
    import { call, put, takeLatest } from "redux-saga/effects";
    import {
      FETCH_USER_REQUEST,
      fetchUserSuccess,
      fetchUserFailure,
    } from "./actions";

    // API 호출 함수
    function fetchUserApi(userId) {
      return fetch(`https://jsonplaceholder.typicode.com/users/${userId}`).then(
        (res) => {
          if (!res.ok) throw new Error("Failed to fetch user");
          return res.json();
        }
      );
    }

    // 제너레이터 함수 (사가)
    function* fetchUserSaga(action) {
      try {
        const user = yield call(fetchUserApi, action.payload);
        yield put(fetchUserSuccess(user));
      } catch (e) {
        yield put(fetchUserFailure(e.message));
      }
    }

    // 액션 감시자 함수, 루트 사가에 등록해서 실행해야 한다.
    export function* rootSaga() {
      yield takeLatest(FETCH_USER_REQUEST, fetchUserSaga);
    }
    ```

    ```js
    // store.js
    import { createStore, applyMiddleware } from "redux";
    import createSagaMiddleware from "redux-saga";
    import { userReducer } from "./reducers";
    import { rootSaga } from "./sagas";

    // saga middleware 생성
    const sagaMiddleware = createSagaMiddleware();

    // store 생성
    export const store = createStore(
      userReducer,
      applyMiddleware(sagaMiddleware)
    );

    // saga 실행
    sagaMiddleware.run(rootSaga);
    ```

    ```jsx
    // App.js
    import React from "react";
    import { useDispatch, useSelector, Provider } from "react-redux";
    import { store } from "./store";
    import { fetchUserRequest } from "./actions";

    function App() {
      const dispatch = useDispatch();
      const user = useSelector((state) => state.data);
      const loading = useSelector((state) => state.loading);
      const error = useSelector((state) => state.error);

      const handleClick = () => {
        dispatch(fetchUserRequest(1)); // userId = 1
      };

      return (
        <div>
          <h1>User Info</h1>
          <button onClick={handleClick}>Fetch User</button>
          {loading && <p>Loading...</p>}
          {error && <p style={{ color: "red" }}>{error}</p>}
          {user && (
            <div>
              <p>Name: {user.name}</p>
              <p>Email: {user.email}</p>
            </div>
          )}
        </div>
      );
    }

    // Provider로 감싸기
    export default function Root() {
      return (
        <Provider store={store}>
          <App />
        </Provider>
      );
    }
    ```

- redux-thunk, redux-saga 비교

  | 상황          | Thunk             | Saga                                    |
  | ------------- | ----------------- | --------------------------------------- |
  | 프로젝트 크기 | 소규모            | 중/대규모                               |
  | 로직 복잡도   | 간단한 API 요청   | 복잡한 흐름 (요청 취소, 순차적 처리 등) |
  | 학습 곡선     | 낮음              | 높음                                    |
  | 코드 스타일   | 함수형, 간결      | 명령형, 유연                            |
  | 테스트        | 상대적으로 어려움 | 테스트 용이                             |

<br>

- Redux vs MobX vs ContextAPI vs Recoil vs Redux toolkit 비교

  (1) Redux : action, reducer, selector, store를 세팅하는 보일러플레이트 코드는 분명 유지보수에 큰 장점을 가지고 있기도 하지만, 상태의 개수가 적더라도 보일러플레이트 코드가 크기 때문에 불편함이 존재한다. 또한 리덕스의 경우 비동기 데이터 처리를 하기 위해서는 사가와 같은 별도의 라이브러리를 추가적으로 사용해야 한다. 또 데이터 관리에 대해 상당히 보수적인 접근방식을 취하고 있어 높은 러닝커브와 큰 보일러플레이트 코드를 가지고 있지만 확장 및 디버깅에 있어서는 엄청난 강점을 가지고 있다.

  (2) MobX : MobX의 경우 리덕스와 달리 store가 여러 개가 될 수 있어 분리가 용이해 편리할 수도 있는 반면 상태 변경시 다수의 스토어가 영향을 받을 수 있다. 또 리덕스와 다르게 스토어의 데이터를 액션의 발행없이 업데이트 할 수 있는데 구현은 쉽고 용이하지만 테스트나 유지보수의 측면에서는 문제를 일으킬 수도 있다. 그렇기에 장기적인 프로젝트, 유지보수 및 확장성을 고려해야 하는 프로젝트의 경우에는 적합하지 않다. 리덕스에 비해 러닝커브가 낮고 보일러플레이트 코드의 양 또한 적기 때문에 프로젝트의 규모가 크지 않은 경우 사용하기 좋다.

  (3) Context API : Context API는 리액트가 자체적으로 가지고 있다. 정적인 데이터 위주로 처리하거나 업데이트가 빈번하지 않을 때 적합하다. 빈번하고 복잡한 업데이트를 처리 시에는 비효율적이다.

  (4) Recoil : 리코일은 아톰과 셀렉터로 이루어져 있다. 아톰은 상태의 단위로, 유니크한 키값으로 구분된다. 해당 아톰을 구독하고 있으면 해당 컴포넌트들만 선택적으로 리렌더링 된다. 아톰의 상태변화는 순수함수를 통해 일어나는데, 이를 셀렉터라고 한다. 셀렉터에서는 비동기처리 뿐만 아니라 데이터 캐싱 기능도 제공하기 때문에 비동기 데이터를 다루기에도 용이하다. 하지만 상대적으로 최근에 나온 라이브러리이기 때문에 안정성 측면에서는 좋지 못할 수도 있다.

  (5) Redux toolkit : 리덕스는 큰 보일러 플레이트 코드를 가지고 있어 상태의 개수가 적어도 작성해야 할 코드가 많다. 또 비동기 데이터 처리를 하기 위해 별도의 라이브러리를 추가로 사용해야한다는 단점이 있다. 리덕스 툴킷은 리덕스가 공식적으로 만든 라이브러리로 다양한 내장 기능을 제공하고 있어 패키지 의존성이 적고 보일러 플레이트 코드가 적다는 장점이 있다.

<br>

- redux toolkit 사용법

  1. store파일을 생성한다. 파일명은 store로 한다. store는 전역 상태 관리가 되는 모든 createSlice를 관리하는 곳이다. store에 reducer에 만들어진 createSlice name을 import해서 넣어줘야한다. 또한 store를 만든 뒤 루트 디렉토리 컴포넌트(ex App컴포넌트)를 Provider 컴포넌트로 감싸 Provider prop를 store={store}로 지정해야한다. 또한 store는 프로젝트에 하나만 존재해야한다.

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

  2. createSlice파일을 생성한다. 파일명은 상관없다. 전역 state와 전역 state를 조작하는 함수를 저장할 createSlice를 만들어야한다. 이 createSlice는 프로젝트에 여러 개가 존재할 수 있다. 전역으로 관리 할 state당 하나가 생성되는 것이다.

  3. createSlice에 initialState는 그냥 state라고 생각하면 된다. 또한 reducers는 이 initialState를 조작할 액션(state값을 조작하는 함수 혹은 state값 재할당 등등 state를 변화시킬 행동)이라고 생각하면 된다.

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

  4. createSlice에 저장 된 action인 reducers로 state를 업데이트하기 위해서는 useDispatch hook을 사용한다. 디스패치라는 이름에서 알 수 있듯이 파라미터를 담아 보내는 역할을 한다. 파라미터를 보내면 createSlice 내부에 reducers에 전달되어 state를 업데이트 시키는 것이다. 또한 initialState나 업데이트 된 state를 사용할 때는 useSelector hook으로 가져와 사용한다.

  5. store에 devTools : 환경변수를 이용해서 현재 서버가 개발자모드인지 프로덕션모드인지를 구분해준다. 보통 boolean타입으로 활용하여 구분한다. devTools: process.env.NODE_ENV !== 'production' 과 같이 사용하는데 이 뜻은 로컬에 있는 환경 변수를 사용하면 true가 되면서 개발 모드가 활성화 된다.

  6. store에 middleware : middleware: (getDefaultMiddleware) => getDefaultMiddleware({ serializableCheck: false }) 와 같이 사용한다. 클라이언트와 서버 중간에 위치해서 중간 기능을 넣는 역할을 한다. getDefaultMiddleware() 는 기본 미들웨어를 적용하기 위해 사용한다. 위와 같이 작성하면 기본 미들웨어에 사용자 미들웨어를 추가하여 함께 사용한다는 뜻이다. 기본 미들웨어는 불변성 검사 미들웨어와 직렬화 기능성 검사 미들웨어가 있다. 불변성 검사 미들웨어는 값을 직접 수정한 경우 (mutation) error를 발생시키는 역할 (redux-immutable-state-invariant)을 하며 직렬화 가능성 검사 미들웨어는 직렬화 할 수 없는 Promise와 같은 객체를 받았을때 error를 발생시키는 역할을 한다.

- 리덕스가 state를 업데이트시킬때 리액트에서는 해당 상태값을 어떻게 감지하는지?

  dispatch를 통해 변경한 state는 이전의 state와 참조 값이 다르기 때문에 virtualDOM에서 상태가 업데이트 됨을 감지할 수 있다.

- 어떤 기준으로 상태관리 여부 구분하는지

  1. Props Drilling이 발생

  2. 여러 컴포넌트에서 공통적으로 사용해야하는 상태의 경우

<br>

### # 상태관리 탑다운 (Top-down) vs 바텀업 (Bottom-up)

- 탑다운 (Top-down) 방식

  - 특징

    - 중앙(store)에서 상태를 한꺼번에 관리하고, 하위 컴포넌트들이 이 상태를 구독해서 사용하는 방식이다.

    - 상태가 루트 레벨에 집중되어 있고, 데이터가 위에서 아래로 흘러가는 구조이다.

    - 대표적 예: Redux, MobX, Context API (중앙 집중식 상태 저장소를 갖고, 컴포넌트는 필요한 데이터만 구독)

  - 장점

    - 상태가 한 곳에 모여 있어 추적과 디버깅이 쉽다.

    - 명확한 흐름(액션 → 리듀서 → 상태 변경 → 뷰 업데이트).

    - 규모가 커질수록 상태 관리 체계적.

  - 단점

    - 초기 설정이 복잡하고 보일러플레이트 코드가 많다 (특히 Redux).

    - 규모가 작거나 간단한 앱에는 과한 설계(오버엔지니어링)일 수 있다.

- 바텀업 (Bottom-up) 방식

  - 특징

    - 상태가 각 컴포넌트 혹은 모듈 단위로 나눠져 독립적으로 관리되고, 필요한 경우 이 상태를 조합하거나 공유하는 방식이에요.

    - 상태가 컴포넌트 단위로 분산되어 있다가, 필요하면 공유/조합.

    - 대표적 예: Recoil, Zustand, Jotai (컴포넌트별 아톰(atom) 단위 상태 관리, 부분적으로 구독 및 조합 가능)

  - 장점

    - 상태가 분산되어 있어 초기 설계와 변경이 유연하다.

    - 필요한 부분만 구독하므로 불필요한 리렌더링 줄일 수 있다.

    - 상태를 작은 단위로 쪼개 관리하며, 협업 시 충돌 줄임.

  - 단점

    - 상태가 여러 곳에 흩어져 있어 전체 데이터 흐름 추적이 어렵다.

    - 상태 간 의존성이 많아질수록 관계 파악이 어려워질 수 있다.

<br>

### # Context API

- Context API란?

  Context는 react 컴포넌트 간의 어떠한 값을 공유할 수 있게 해주는 기능이다. 대부분 전역 상태 관리를 할 때 사용한다고 알고 있지만 꼭 전역적인 값만이 아닌 react 컴포넌트에서 Props가 아닌 또 다른 방식으로 컴포넌트 간에 값을 전달하는 방법이다.

- 기본적인 사용법

  - Provider

    createContext 라는 함수를 불러와 context 객체를 만들 수 있다. 그 후 context의 객체의 provider 컴포넌트로 value를 전달해 줄 컴포넌트를 래핑한 뒤 해당 컴포넌트의 하위 컴포넌트로 value를 공급해줄 수 있다. 이 때 해당 context의 value를 사용하는 컴포넌트에서는 useContext hook을 통해서 사용할 수 있는데 이 때 인자로 이전에 createContext 함수를 통해 생성한 context를 넘겨주어 사용할 수 있다. 또한 커스텀 훅을 사용해서 간결하게 사용하도록 할 수 있다.

    ```javascript
    // ContextParent.tsx
    import { createContext } from "react";
    import ContextChildrenOuter from "./contextChildrenOuter";

    const MyContext = createContext("");

    const ContextParent = () => {
      const props = "Hello World";

      return (
        <MyContext.Provider value={props}>
          <ContextChildrenOuter />
        </MyContext.Provider>
      );
    };

    export default ContextParent;
    export { MyContext };

    // ContextChildrenInner.tsx
    import { useContext } from "react";
    import { MyContext } from "./contextParent";

    const ContextChildrenInner = () => {
      const value = useContext(MyContext);

      return <div>{value}</div>;
    };

    export default ContextChildrenInner;
    ```

  - Consumer

    Context 객체의 Consumer 컴포넌트는 context 변화를 구독하는 컴포넌트이다. context의 자식은 함수(컴포넌트)이어야 한다. 이 함수(컴포넌트)가 가지는 context 값은 가장 가까운 provider의 값이다. 만약 상위 provider가 없다면 createContext()에서 정의한 defaultValue를 가진다. 만약 여러 컴포넌트를 구독하려면 아래와 같이 Consumer 내부에 또다른 Consumer를 정의하는 방법으로 context를 내려줘야한다.

    ```javascript
    <ThemeContext.Consumer>
      {(theme) => (
        <UserContext.Consumer>
          {(user) => <ProfilePage user={user} theme={theme} />}
        </UserContext.Consumer>
      )}
    </ThemeContext.Consumer>
    ```

- Context API가 있는데 왜 전역 상태 관리 라이브러리를 사용할까?

  - Context API 한계

    - 리렌더링 성능 문제 : Context는 값이 바뀌면 해당 Context를 사용하는 모든 컴포넌트를 리렌더링합니다. → 세분화된 구독 불가

    - 비동기 처리 어려움 : Context 자체는 비동기 로직(예: API 호출)을 처리하는 구조가 없음. 추가적으로 useEffect 등으로 직접 구현해야 함

    - 복잡한 상태 구조 관리 어려움 : 상태가 커지고 구조가 복잡해질수록 Context만으로 상태를 관리하기 어려워짐 (상태 분리, 리듀서, 미들웨어 등 없음)

    - 미들웨어/디버깅 도구 부족 : Redux 같은 라이브러리는 강력한 DevTools, 미들웨어(logging, 비동기 처리 등) 지원이 풍부함

  - 전역 상태 관리 라이브러리를 쓰는 이유

    - 세분화된 상태 구독 : Recoil, Zustand 등은 특정 “상태 단위”만 구독 → 필요한 컴포넌트만 리렌더링됨

    - 모듈화 / 분리된 상태 관리 : 여러 slice, atom, store로 상태를 역할별로 나눠 관리 가능

    - 비동기 로직 내장 처리 : Redux Toolkit의 createAsyncThunk, Recoil의 selector, Zustand의 store 함수 등 비동기 처리 내장

    - 디버깅 & DevTools : 상태 추적, 시간 이동 디버깅, 로깅 등 가능 (Redux DevTools 등)

    - 미들웨어 지원 : Redux의 middleware, Recoil effects 등으로 로깅, 인증 체크, 로컬 스토리지 연동 등 쉽게 구현 가능

  - Context API 언제 사용?

    - 정적인 전역 값 공유

      - Context 값을 구독하는 컴포넌트는 Context 값 변경 시 리렌더링이 발생한다. 그렇기 때문에 자주 변경이 발생하는 값보다는 정적인 값을 공유할 때 적합하다.

      - 예시 : 로그인한 사용자 정보 (auth, user), 테마 설정 (darkMode, theme), 언어 (locale, i18n) 등

    - props dlilling을 피할 때

      - 만약 Context 값을 직접 구독하지 않는 중간 컴포넌트 그 자체로는 안전함, 다만 부모가 리렌더링되면 자식도 같이 리렌더링될 수 있음. 이를 피하려면 React.memo, useMemo, useCallback 등의 최적화 도구를 적절히 써야 한다. 즉 부모의 Context 값 변경 시 리렌더링 발생을 막기 위해 메모이제이션 해야한다.

<br>

### # Redux vs ContextAPI

| 구분                     | **Redux**                                      | **Context API**                                |
| ------------------------ | ---------------------------------------------- | ---------------------------------------------- |
| **1. 개념**              | Flux 아키텍처 기반의 상태 관리 라이브러리      | React 내장 전역 상태 공유 기능 (Provider 패턴) |
| **2. 상태 저장 위치**    | 단일 전역 `store` 객체에서 관리                | 여러 `Context` 객체를 만들어 관리 가능         |
| **3. 데이터 흐름**       | Action → Reducer → Store (단방향)              | Context Provider → Consumer (단방향)           |
| **4. 상태 변경 방식**    | `dispatch(action)`을 통해 reducer 함수로 변경  | `setState` 또는 `useReducer`로 변경            |
| **5. 보일러플레이트**    | 많음 (action, reducer, store 설정 등)          | 적음 (Context 생성 + Provider 사용)            |
| **6. 학습 곡선**         | 상대적으로 높음                                | 낮음 (React 기본 API)                          |
| **7. 미들웨어 확장성**   | 강력함 (redux-thunk, redux-saga 등)            | 없음 (비동기 로직은 직접 구현해야 함)          |
| **8. 디버깅 도구**       | 매우 강력 (Redux DevTools 등)                  | 기본적으로 없음                                |
| **9. 성능**              | 선택적 구독 가능 → 리렌더링 최소화             | Context를 구독하는 컴포넌트는 전부 리렌더링됨  |
| **10. 대규모 앱 적합성** | ✅ 매우 적합                                   | ❌ 성능 저하 우려 있음                         |
| **11. 상태 분리 구조화** | Slice 단위로 분리해 관리 (Redux Toolkit 등)    | 여러 Context로 분리 가능하나 복잡해질 수 있음  |
| **12. 용도 예시**        | 장바구니, 사용자 권한 관리, 비동기 API 관리 등 | 다크모드, 언어 설정, 로그인 여부 등 간단 상태  |

<br>

### # Headless UI

- Headless UI란?

  프론트엔드 웹 개발을 하다보면 생산성 향상을 위해 UI 라이브러리를 사용하고는 한다. 일반적인 Component 기반 UI 라이브러리는 개발자가 해당 컴포넌트를 바로 사용할 수 있도록 고유의 스타일이 적용되어있는데 거의 모든 사용되는 서비스 디자인에 맞게 커스텀이 필요하게 된다. 하지만 커스텀하는 과정 중 한계에 부딪히는 경우가 발생할 수 있고 커스텀이 까다로운 경우도 발생할 수 있다. 이러한 경우 Headless UI 라이브러리를 사용할 수 있다.

- Component 기반 UI 라이브러리

  Component 기반 UI 라이브러리는 기능과 스타일이 존재하는 라이브러리, 디자인이 그렇게 중요하지 않고, 커스텀할 곳이 많지 않다면 Component 기반 UI 라이브러리를 사용하면 된다.

  - 장점

    - 바로 사용할 수 있는 마크업과 스타일이 존재

    - 설정이 거의 필요 없음

  - 단점

    - 마크업을 자유롭게 할 수 없음

    - 스타일은 대부분 라이브러리에 있는 테마 기반으로만 변경할 수 있어 한정적임

    - 큰 번들 사이즈

- Headless UI 라이브러리

  Headless UI 라이브러리는 기능은 있지만 스타일이 없는 라이브러리, 반응형에 따라 디자인이 달라지고, 기능 변경이나 추가가 많이 발생한다면 Headless UI 라이브러리가 유지보수에 더 좋을 수 있다.

  - 장점

    - 마크업과 스타일을 완벽하게 제어 가능

    - 관심사의 분리로 인한 유지보수 용이

    - 모든 스타일링 패턴 지원(ex. CSS, CSS-in-JS, UI 라이브러리 등)

    - 작은 번들 사이즈

  - 단점

    - 추가 설정이 필요함

    - 마크업, 스타일 혹은 테마 모두 지원되지 않음

- Headless Component 만들기

  - Compound Component

    사용되는 컴포넌트들의 상태(state) 값을 공유할 수 있게 만들어주는 패턴이다. (ex ContextAPI 활용)

  - Function as Child Component

    자식에 어떤 것이 들어올지 예상할 수 없기 때문에 children prop으로 받아 그대로 전달한다.

  - Custom hooks

    React를 사용해본 사람이라면 가장 익숙할 법한 Custom hooks이다.

<br>

### # Bundling과 code splitting

- 번들링(Bundling)

  서로 연관있는 여러 파일을 하나의 파일로 병합(js, img, scss 등)하는 것을 말한다. 하나로 병합 된 번들로 요청/응답을 받음으로써 HTTP 요청 횟수를 줄일 수 있다. 대표적인 모듈 번들러로 웹팩이 있고 그 외에 비트, 롤업, 파셀 등도 있다.

- 코드 스플리팅(code splitting)

  프로젝트 규모가 커지면 번들 사이즈도 커지게 된다. 그렇게 되면 성능 저하가 일어날 수 있다. 이럴 때 코드 스플리팅을 사용한다. 코드 스플리팅은 하나의 메인 번들을 여러 개의 번들(청크)로 나누어준다. 코드 스플리팅으로 번들을 나눈 후 실제 로드될 화면에 필요한 번들 파일만 불러오고 나머지 번들 파일은 호출하지 않고 지연시키는 비동기 로딩 방식으로 로딩 속도를 향상시킬 수 있다.

- 코드 스플리팅 적용 방법

  (1) dynamic import 문법 사용 : 자바스크립트 함수 비동기 로딩 시 import() 함수 형태로 메서드 안에서 사용하게 되면 필요할 때 해당 스크립트를 불러와서 사용할 수 있다. import를 함수로 사용하면 Promise를 반환한다. nextjs에서는 기본적으로 page 디렉토리 내부 컴포넌트들은 빌드 단계에서 자동으로 코드스플리팅된다. 또한 다른 컴포넌트들은 next/dynamic의 dynamic 메소드를 사용하여 구현할 수 있다. 첫번째 인자로 import 함수, 두번째 인자로 옵션을 지정할 수 있다. 옵션에서는 로딩 시 보여줄 UI, SSR 여부 등을 지정할 수 있다.

  ```js
  // react.js
  const onClick = () => {
    import("./subPage").then((result) => result.default());
  };

  // next.js
  import dynamic from "next/dynamic";

  const DynamicHeader = dynamic(() => import("../components/header"), {
    loading: () => <p>Loading...</p>,
  });

  export default function Home() {
    return <DynamicHeader />;
  }
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

### # React Native

- 리액트 네이티브 개발을 해본 적이 있는지

  부트캠프 교육 시 한달 정도 기업협업에 나가 경험해 본 경험이 있다. react native, typescript, mobx 등의 기술을 사용했었다. 마일리지를 이용하여 기프티콘을 구매하는 서비스였는데 기능을 추가하는 작업을 했었다. 카카오맵API, 웹뷰를 활용하여 지도 주소 검색 기능, 지번 도로명 주소 변환, 새 페이지 추가, 작은 버그 수정 등의 작업을 했었다. 또한 루머라는 회사에서 근무할 당시 react native webview를 활용해본 경험이 있다.

- 웹뷰

  웹뷰(WebView) 는 모바일 애플리케이션 안에서 웹 콘텐츠(웹페이지나 웹 앱)를 표시할 수 있는 뷰(View) 를 말합니다. 즉, 앱 내에 웹 브라우저 창을 삽입하는 것처럼 동작하며, HTML, CSS, JavaScript로 작성된 콘텐츠를 앱에서 바로 렌더링할 수 있게 해준다. 안드로이드와 iOS 모두에서 제공하고 있다. 웹뷰를 사용한 장점은 배포 주기를 빠르게 가져갈 수 있다는 점이다.

- 웹뷰 사용 경험

  웹뷰에 보여질 카카오 map api, 버튼 등을 생성하여 프로젝트를 따로 만들어 준 뒤 배포하고 웹뷰를 생성할 프로젝트에서 WebView 컴포넌트와 WebView 컴포넌트의 source 옵션을 통해 배포된 프로젝트와 연결하고 다른 옵션들을 통해 웹뷰에서 받은 주소 데이터를 저장하고, 로딩 시 스피너를 구현하였다.

<br>

### # Progressive rendering

- 서버에서 중요한 컨텐츠를 렌더링한 후, 중요하지 않은 콘텐츠를 기다리지 않고 클라이언트로 스트리밍하는 기술이다. 그런 다음 서버에서 렌더링되면 나중에 중요하지 않은 콘텐츠를 스트리밍한다. 관련 기술로는 Image Lazy Loading, DOMContentLoaded 이벤트의 사용 등이 있다.

<br>

### # Link, NavLink, useNavigate 차이

- Link

  페이지 이동 시 사용

  ```javascript
  <Link to="경로">내용</Link>
  ```

- NavLink

  페이지 이동 시 사용, Link 와의 차이점은 자체적으로 boolean을 반환하는 isActive 속성을 가지고 있으며 현재 어떤 페이지에 있는지 시각적으로 표시할 때 사용 (탭 메뉴 등)

  ```javascript
  <NavLink
    to="/"
    className={({ isActive }) => (isActive ? classes.active : undefined)}
  >
    Home
  </NavLink>
  ```

- useNavigate

  페이지 이동 시 사용하는 hook, 페이지 이동 시 추가 로직을 사용할 수 있다. 또 이동되는 페이지에 state를 전달할 수 있다.
  또 해당 페이지를 새로 불러오거나, 이전 페이지, 다음 페이지로의 이동을 편하게 할 수 있다. `ex) navigate(0), navigate(-1), navigate(+1)`

  ```javascript
  const Page = () => {
    const navigate = useNavigate();

    const navigateHandler = () => navigate("/");

    return <button onClick={navigateHandler}>Go Home</button>;
  };
  ```

<br>

### # a태그와 link 컴포넌트 차이

- a태그는 서버 사이드 라우팅 방식으로 페이지 이동 시 페이지를 새로 불러오고 새로 불러오기 때문에 모든 데이터를 다시 요청한다. 반면 Link 컴포넌트는 클라이언트 사이드 라우팅 방식으로 페이지 이동 시 HTML5 History API를 사용하여 브라우저의 주소만 바꿀 뿐, 페이지를 새로 불러오지는 않고 필요한 데이터만 요청한다.

<br>

### # 성능 측정 방법

- 함수 성능 측정

  perpomance.now, console.time

- 컴포넌트 렌더링 속도 및 리렌더링 측정

  react developer tools (크롬 익스텐션 설치 후 개발자 도구에 profiler탭 활용 (ms 단위))

- 웹 페이지 퍼포먼스

  개발자 도구에 Lighthouse탭 활용 (웹 페이지 퍼포먼스, 접근성, SEO, 표준 모범 사례 점수 등을 측정)

<br>

### # 성능 개선 지표

- 브라우저 기준의 측정

  브라우저 기준의 성능 측정은 전통적인 성능 측정 방식으로 브라우저에서 발생하는 이벤트를 사용하는 것이다. 웹 페이지가 로딩될 때 `DOMContentLoaded`, `load` 이벤트가 발생하는데 각 이벤트가 발생하는 시점으로 성능을 측정하는 것이다. 내비게이션 타이밍 모델에서 `DOMContentlLoaded` 이벤트, `load` 이벤트 발생 시점이 빠를수록, 그리고 두 이벤트 발생 구간의 폭이 좁을수록 성능이 좋다고 말한다. 하지만 최근에 SPA(Single Page Application)에서는 웹 페이지에 포함된 적은 양의 HTML로 DOMContentLoaded, load 이벤트가 일찍 발생할 수 있으나, 이벤트가 발생한 이후에도 수많은 스크립트 실행으로 인해 여전히 "느린 로딩"이 존재한다. 이러한 이유로 사용자 기준의 새로운 성능 측정 방식이 필요하게 되었으며 사용자 기준의 성능 측정 방식을 활용한다.

- 사용자 기준의 측정

  사용자 기준의 성능 측정은 사용자에게 콘텐츠를 보여주는 여러 시점을 기반으로 한다. 의미 있는 콘텐츠가 처음 보이는 시점이 빠를수록 성능이 좋다고 판단하며, 이 시점을 앞당길 수 있도록 최적화해야 한다. 해당 시점을 측정하기 위해서 크롬 개발자 도구를 활용할 수 있다.

- 성능 측정 도구 중 크롬 개발자 도구

  - Network

    Network 패널에서는 웹 페이지가 로딩되는 동안 요청된 리소스의 상태를 차트 형태로 확인할 수 있으며, 리소스 최적화 상태를 비교할 때 사용한다. Performance 패널과 같이 레코딩하고, 레코딩이 끝나면 Overview와 Request Table에 리소스 요청 정보가 나타난다. 이때 리소스 목록은 시간순으로 정렬된다. 또한 Request Table에 요청을 개별로 클릭하여 Timing 탭을 클릭하면 리소스 요청별 서버 요청 대기 시간을 확인할 수 있다.

  - Performance

    Performance 패널에서는 앞서 살펴본 웹 페이지 로딩 단계를 차트 형태로 살펴볼 수 있다. 웹 페이지가 로드되는 과정을 레코딩하고 단계마다 걸리는 시간을 확인할 수 있다. 로딩 과정에서 최적화가 필요한 부분을 찾을 때 사용한다.

  - Lighthouse

    - Lighthouse란?

      Lighthouse는 구글에서 제공하는 웹 페이지 품질 개선을 위한 오픈 소스로 자동화 도구이다. Lighthouse는 사이트의 성능, 접근성, SEO 등에 대한 전반적인 진단을 해준다. 주의할 점은 정확한 측정을 위해서는 항상 프로덕션 환경에서 측정하는 것이 좋다.

    - Performance

      웹 페이지의 로딩 속도 등 실제 성능을 측정

    - Best practices (https://developer.chrome.com/docs/lighthouse/best-practices/)

      웹 페이지가 웹에 대한 표준 모범 사례(Best practices를 따라 개발되었는지)를 따르고 있는지 확인한다. 웹 애플리케이션을 가동할 때 콘솔에 오류가 출력되진 않는지, 더는 사용하지 않는 API를 호출하고 있지 않은지, HTTPS를 통해 해당 페이지에 접근할 수 있는지와 같은 항목을 확인한다.

    - Accessibility

      접근성 확인. 폰트 사이즈, 메뉴간 간격 등을 측정

    - Progressive Web App (PWA)

      웹과 네이티브 앱의 기능 모두의 이점을 가지도록 만들어진 서비스인지 체크

    - SEO

      Search Engine Optimization의 약자로 검색 엔진 수집 최적화 측정

  - Lighthouse Performance의 여섯가지 metric과 가중치

    - FCP (First Contentful Paint), 10%

      페이지 로드가 시작된 후 의미있는 컨텐츠가 화면에 렌더링 완료될 때까지의 시간 (예: 의미있는 컨텐츠라는 것은 `<meta>`, `<link>`, `<script>`와 같은 메타데이터 관련 요소가 아닌 사용자 눈에 보이는 `<img>`, `글자(텍스트 노드)가 입력되어 있는 <span> or <p>` 등, 즉 화면에 실제 그려지는 요소 = 의미있는 컨텐츠)

    - LCP (Largest Contentful Paint), 25%

      가장 큰 콘텐츠 요소가 화면에 완전히 렌더링되는 시점 (보통 가장 큰 이미지 혹은 텍스트)

    - TBT (Total Blocking Time), 30%

      FCP와 TTI 사이에 일어난 작업 중 메인 스레드가 Long Task(50ms 초과 작업)로 인해 사용자 입력을 막고 있었던 시간의 총합 (예: 즉 의미있는 컨텐츠가 화면에 그려진 후 사용자 상호작용이 가능하게 된 시간 중 긴 작업으로 인해 사용자 상호작용이 블로킹 된 시간)

    - CLS (Cumulative Layout Shift), 15%

      예상치 못한 레이아웃 이동의 누적 점수, 레이아웃 변화가 예상되지 않았을 때만 측정 (예: 이미지 높이 미지정, 폰트 로딩 지연 등으로 인해 클릭하려던 버튼이 밀리는 현상 등.)

    - SI (Speed Index), 10%

      뷰포트 내의 콘텐츠가 콘텐츠가 시각적으로 표시되는 진행 속도를 프레임을 기준으로 측정(예: 리로드되는 페이지의 비디오를 캡쳐하여 프레임 간의 속도를 계산)

    - TTI (Time To Interactive), 10%

      페이지가 완전히 상호작용 가능한 상태가 된 시점

  - LCP 최적화 방법

    1. 서버 최적화
    2. CDN 사용
    3. 자주 변하지 않는 데이터의 경우 캐시 사용 (react query, apollo client, http header cahce-control 헤더 -> 유효 기간 내 요청 시 메모리에서 캐시를 읽어와 사용)
    4. 이미지 최적화, 외부 폰트 경량화(서브셋 폰트)
    5. SSR, SSG 사용
    6. 코드 스플리팅

  - FCP 최적화 방법

    1. 데이터 압축 (번들링)
    2. HTTP/2 사용 (요청 병렬 처리)
    3. 리로드 할 필요 없는 콘텐츠를 캐싱
    4. 코드 경량화와 코드 스플리팅
    5. 라이브러리 정리 (트리쉐이킹, 패키지 매니저 변경, 필요없는 라이브러리 제거)

  - Next.js에서 Lighthouse 사용하기

    Next.js 공식 도큐에서도 lighthouse를 통해 웹 성능을 체크하는 방식을 설명하고 있다. lighthouse의 정확한 측정을 위해서는 개발 환경이 아닌 항상 배포 환경에서 측정 해야한다는 것이다. 이미 배포된 웹 페이지들은 상관 없지만 개발중인 페이지들은 로컬에서 `yarn build` 혹은 `npm run build`로 빌드를 한 후, `yarn start` 혹은 `npm run start`로 실행해서 측정해야한다.

<br>

### # useMemo, useCallback

- 메모제이션이란?

  useMemo와 useCallback에서는 메모이제이션이라는 개념이 나오는데 메모이제이션이란 이전 값을 메모리에 저장해두어 동일한 계산의 반복을 제거해 빠른 처리를 가능하게 하는 기술이다. useMemo는 메모이제이션 된 값을 반환하고 useCallback은 메모이제이션 된 함수를 반환한다. useMemo와 useCallback은 의존성 배열에 넘겨준 값이 변경되었을 때만 메모리제이션된 값을 다시 계산하고 아닌 경우 동일한 값을 반환한다.

- useMemo를 사용해야 하는 경우

  - 값의 연산 비용이 높은 경우

  - 리렌더링 시 동일 계산 반복을 방지할 때

  - 리렌더링 시 객체, 배열 등의 참조 주소를 유지시키기 위해

    ```jsx
    const Child = React.memo(({ items }) => {
      console.log("자식 렌더링!");
      return <div>{items.join(", ")}</div>;
    });

    function Parent({ length }) {
      const items = useMemo(() => Array.from({ length }), [length]);

      return <Child items={items} />;
    }
    ```

- useCallback을 사용해야 하는 경우

  - 함수 내부 연산 비용이 높은 경우

  - 리렌더링 시 함수의 참조 주소를 유지시키기 위해

    - 부모 컴포넌트의 state 변경 시 자식 컴포넌트 props와 관련없는 state 임에도 부모 state가 변경되었기 때문에 자식 컴포넌트도 리렌더링된다. 이런 경우 React.memo를 활용해서 props가 변경되지 않는 경우 자식 컴포넌트의 리렌더링을 막을 수 있다. 하지만 props가 함수인 경우에는 다르다. props가 함수인 경우 부모 state가 변경 시 함수는 재생성되기 때문에 이전 참조와 다른 참조를 가리키게 된다. 그렇기 때문에 props가 같은 형태의 함수임에도 리렌더링이 발생한다. 이 때 useCallback을 사용하여 함수의 동등성(참조 유지)을 유지시켜준다. useCallback으로 함수의 동등성을 유지시켜준 상태로 자식 컴포넌트를 React.memo로 래핑하면 참조가 변하지 않았기 때문에 메모이제이션 된 컴포넌트를 사용하여 리렌더링이 발생하지 않는다.

    ```jsx
    import React, { useState, useCallback } from "react";

    // 자식 컴포넌트 (React.memo로 감싸져 있음)
    const Child = React.memo(({ onClick }) => {
      console.log("Child 렌더링");
      return <button onClick={onClick}>Click me</button>;
    });

    // 부모 컴포넌트
    function Parent() {
      const [count, setCount] = useState(0);

      // useCallback으로 함수 메모이제이션
      const handleClick = useCallback(() => {
        console.log("버튼 클릭!");
      }, []); // 의존성 없으니 한 번만 생성

      return (
        <div>
          <p>Count: {count}</p>
          {/* 버튼 눌러도 handleClick 함수 참조가 변하지 않음 */}
          <Child onClick={handleClick} />
          <button onClick={() => setCount(count + 1)}>증가</button>
        </div>
      );
    }

    export default Parent;
    ```

  - callback ref가 필요할 때 사용, 자식 컴포넌트의 ref를 다룰 때 forwardRef를 사용하는데 이 때 useEffect로 ref를 핸들링하면 자식 컴포넌트 내부 렌더링이 완료되기 전 ref의 값은 null이 되어 문제가 발생한다. 이럴 때 callback ref를 사용하여 해결할 수 있다. 간단하게 기본적으로 ref는 렌더링 여부를 체크할 수 없는데 useCallback을 활용하여 렌더링과 연관시켜 작업할 수 있게 되는 것이다. 즉 컴포넌트 생명주기에 바인드되던 ref를 DOM 노드의 생명주기로 바인드시키는 방식이다.

    ```jsx
    import React, {
      useState,
      useRef,
      useCallback,
      forwardRef,
      useEffect,
    } from "react";

    // forwardRef를 사용한 자식 컴포넌트
    const Child = forwardRef((props, ref) => {
      return <input ref={ref} placeholder="이곳에 포커스 됩니다" />;
    });

    function Parent() {
      const [count, setCount] = useState(0);

      // callback ref를 useCallback으로 메모이제이션
      const inputRef = useCallback((node) => {
        if (node !== null) {
          // node는 실제 DOM 요소(input)
          node.focus(); // 렌더링된 시점에 포커스 처리 가능
          console.log("Input에 포커스 됨!");
        }
      }, []);

      // 만약 useRef + useEffect로 했다면?
      /*
        const inputRef = useRef(null);
        useEffect(() => {
          if (inputRef.current) {
            inputRef.current.focus();
          }
        }, []);
        */

      return (
        <div>
          <Child ref={inputRef} />
          <button onClick={() => setCount(count + 1)}>증가: {count}</button>
        </div>
      );
    }

    export default Parent;
    ```

- useMemo와 useCallback을 사용하지 말아야 하는 경우

  - 연산이 복잡하지 않은 값이나 함수의 경우, 연산이 복잡하지 않은 경우 메모이징하는 것이 오히려 메모리 낭비가 될 수 있다.

  - 의존성 배열의 값이 자주 변화하는 경우, 자주 변하는 값이나 함수의 경우 메모이징하는 의미가 없다.

  - 의존성 배열의 요소가 많은 경우, 의존성 배열의 요소가 많은 경우 자주 변하는 값이나 함수일 확률이 높기 떄문에 메모이징하는 의미가 없다.

<br>

### # HOC(High Order Component)

- HOC(High Order Component)는 고차 컴포넌트이며 컴포넌트를 인자로 전달받아 컴포넌트를 반환하는 컴포넌트이다. 보통 관심사 분리, 기능 확장, 고차 컴포넌트 재사용 등을 위해 사용한다.

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

### # 고차함수(Higher order function)

- 고차 함수는 함수를 인자로 전달받거나 함수를 결과로 반환하는 함수를 말한다.

<br>

### # **컴포넌트와 엘리먼트의 차이점은?**

- 엘리먼트

  DOM element(태그)를 나타내는 일반적인 객체

- 컴포넌트

  props를 받아 DOM 엘리먼트의 정보를 담은 react 엘리먼트 객체를 출력하는 함수 혹은 클래스이다. react에서 index 파일 내부 ReactDOM.createRoot 함수를 통해 컨테이너 돔(ex `<div id="root"></div>`)을 지정하고 컴포넌트에서 return 되는 react 엘리먼트 객체를 컨테이너 돔의 메소드인 render 메소드를 통해 컨테이너 돔 내부에 렌더링한다.

  ```javascript
  // 컨테이너 돔 지정
  const root = ReactDOM.createRoot(document.getElementById("root"));

  const element = <h1>Hello, world</h1>; // DOM 엘리먼트의 정보를 담은 리액트 엘리먼트 객체 생성
  root.render(element); // 컨테이너 돔 내부에 리액트 엘리먼트 렌더링
  ```

<br>

### # useEffect와 useLayoutEffect 차이

<br>

- 둘의 사용법은 완전히 동일하다. 둘의 차이점은 useEffect는 DOM이 화면에 그려진 후(브라우저 렌더링 단계 중 페인트 완료 후)호출되고 useLayoutEffect는 DOM을 그리기 전(렌더, 커밋 페이즈 단계가 완료 된 후 브라우저의 페인트 단계 전) 호출된다.

  예를 들어 useEffect 내부에서 state를 업데이트하여 DOM에 내용을 채운다고 가정했을 때 DOM을 렌더링 한 후 useEffect를 호출하여 state를 업데이트하고 리렌더링을 수행하여 DOM에 내용을 채우는 것이다. 하지만 DOM에 갯수가 많아지고 복잡해지면 렌더링 시간이 증가하게 되어 useEffect 사용 시 state가 업데이트 되지 않은 상태를 사용자가 볼 위험이 생긴다.

  이런 경우 useLayoutEffect를 사용하여 문제를 해결할 수 있다.

  ```
  // useEffect
  (1) `<div>그의 이름은 이며, 나이는 0살 입니다.</div>` 를 페인트
  (2) useEffect 이펙트 내부의 setAge(31), setName("재민") 호출
  (3) 리렌더링 수행 -> `<div>그의 이름은 재민이며, 나이는 31살 입니다.</div>`

  // useEffectLayout
  (1) useEffectLayout 이펙트 내부의 setAge(31), setName("재민") 호출
  (2) 리렌더링 수행 -> `<div>그의 이름은 재민이며, 나이는 31살 입니다.</div>`
  ```

<br>

### # useReducer

- useReducer

  useReducer는 useState와 같이 state를 관리하고 업데이트할 수 있는 hook이다. useState와의 차이는 useReducer는 state 변경에 관한 로직을 묶어서 관리한다. useReducer를 사용하면 state 관련 로직을 묶어서 사용하므로 가독성을 향상시키고 유지보수를 용이하게 할 수 있다. 만약 state가 단순한 값이 아닌 여러 값으로 변경된다면 useReducer를 사용하는 것이 좋을 수 있다. 사용법은 redux와 비슷하다. reducer를 생성하고 useReducer에 인자로 생성한 리듀서와 state 초기 값을 전달한다. 그리고 setState 대신 dispatch를 통해 action 타입을 전달해 state를 업데이트시킨다.

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

### # SVG 컴포넌트화

- svgr/webpack 라이브러리를 활용하여 SVG를 컴포넌트로 사용할 수 있다. SVG를 컴포넌트로 사용하는 경우 크기, 색상 등의 커스텀을 할 수 있어 재사용성이 증가된다.

<br>

### # 커스텀 훅(custom hook)

- 커스텀 훅이란 개발자가 만들어 사용하는 훅으로 특정 상태 관리나 로직을 재사용하도록 별도의 파일로 분리하여 처리하는 훅을 이야기한다. 커스텀 훅의 사용 이유는 관심사의 분리, 특정 상태 관리 및 로직의 재사용 등의 이유로 사용한다.

  ```javascript
  import { useState, useCallback } from "react";

  function useInputs(initialForm) {
    const [form, setForm] = useState(initialForm);
    // change
    const onChange = useCallback((e) => {
      const { name, value } = e.target;
      setForm((form) => ({ ...form, [name]: value }));
    }, []);
    const reset = useCallback(() => setForm(initialForm), [initialForm]);
    return [form, onChange, reset];
  }

  export default useInputs;
  ```

<br>

### # 로그인 버튼을 누른 후 처리가 지연 되고 있는 순간에 다른 UI 버튼을 클릭한다면 처리는 어떻게 되는가? 비동기 처리라고 한다면 이건 문제가 있지 않은가? (API 요청 처리 전 컴포넌트 언마운트)

- 대부분 로그인이 필요한 서비스의 경우 로그인 하지 않은 사용자가 UI를 조작하게 되면 로그인 페이지로 리다이렉트 시키는데 만약 비동기 통신을 통해 액세스 토큰을 받아오는 로그인 과정이 지연되는 경우 스피너같은 로딩 화면을 띄워 토큰을 받아오기 전 사용자가 다른 UI를 누를 수 없도록 방지할 것 같다. 만약 예외 처리를 하지 않은 경우 API를 요청한 컴포넌트가 언마운트되면 이후 동기적으로 처리하는 로직에서 문제가 발생하거나 메모리 누수가 발생할 수 있다.

- 만약 특정 컴포넌트 내에서 API 요청 후 페이지를 이동하여 해당 컴포넌트가 언마운트되는 경우 후속 처리에서 setState를 하는 경우 메모리 누수 이슈가 발생할 수 있다. 즉 처리 전 언마운트 되기 때문이다. 이럴 때 useEffect의 cleanup으로 처리해줘야한다.

<br>

### # 제어 컴포넌트와 비제어 컴포넌트 차이

- 제어 컴포넌트

  컴포넌트의 state나 props로 입력 폼 값이 제어되는 컴포넌트이다. 예시로 input의 value 값을 useState로 값을 업데이트 시키는 것이 대표적인 제어 컴포넌트의 예시이다. 데이터와 UI가 항상 동기화되어 입력 값 발생 시 계속 리렌더링 되어 최신화가 유지된다. 유효성 검사나 조건부 버튼 활성화에 사용한다.

  ```jsx
  // 제어 컴포넌트 예시
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

- 비제어 컴포넌트

  DOM 자체에서 입력 폼 데이터를 다루는 컴포넌트이다. 예시로 input에 ref 속성을 할당하여 입력 폼을 제출할 때 값을 업데이트 시키는 것이 대표적인 비제어 컴포넌트의 예시이다. 데이터와 UI가 동기화되어 있지 않아 입력 값 발생 시 리렌더링 되지 않고 입력 폼을 제출할 때 렌더링된다. 일회성 정보 검색이나 제출 시 값 검증에 사용한다.

  ```jsx
  // 비제어 컴포넌트
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

### # 리액트의 렌더링 성능 향상 방법

1. 렌더링 성능 측정

- react developer tools 익스텐션으로 컴포넌트 렌더링 성능을 측정하여 개선한다.

- 구글 라이트하우스를 활용하여 FCP, LCP, TBT, CLS, SI, TTI 등의 성능을 측정하고 개선한다. FCP는 최소 3초 LCP는 최소 4초 이내에 들어야한다. 해당 시간이 벗어나면 사용자가 서비스에서 이탈할 확률이 증가한다.

- 함수 성능 측정은 perpomance API나 console.time 메소드를 활용하여 측정하고 개선한다.

2. useMemo, useCallback, React.memo

- useMemo, useCallback, React.memo 등을 사용하여 값, 함수, 컴포넌트를 메모이제이션하여 재사용한다.

3. 코드 스플리팅

- Lazy와 Suspense를 사용하여 코드 스플리팅하고 번들의 크기를 줄여 당장 필요한 컴포넌트만 우선적으로 렌더링하도록 한다.

4. 이미지 사이즈 최적화

- 이미지를 압축율이 좋은 이미지 포맷으로 변경한다. 예를 들면 avif 포맷으로 변경할 수 있다. 하지만 이와 같은 경우 해당 이미지 포맷의 호환되는 브라우저 확인은 필수이다. 다만 nextjs에서는 이미지 컴포넌트가 자동으로 사용자 브라우저에 호환되는 이미지 포맷으로 변환해주기 때문에 확인이 불필요하다.

- 이미지를 사용자에게 보여지는 레이아웃 크기를 고려하여 사이즈를 줄인다. 예를 들면 canvas를 사용하여 이미지를 리사이징해서 사용 및 저장하거나 img 태그의 srcset 속성을 활용하여 뷰포트 별 이미지를 제공할 수 있다. 또한 고정 사이즈를 사용하여 리플로우를 최소화할 수 있다. 또한 nextjs의 경우 기본적으로 사용하는 이미지 로더를 squoosh에서 sharp로 바꾸는 것만으로도 이미지 최적화에 도움이 된다. -> 이미지 최적화 라이브러리인 sharp의 경우 next15 버전부터 자동으로 sharp를 사용하므로 수동으로 설치할 필요가 없다.

- IntersectionObserver API와 같이 뷰포트를 감지하는 API를 활용하여 해당 이미지 보여져야 할 때 서버에 요청을 보내 이미지를 가져오는 이미지 레이지 로딩을 활용한다.

5. 애니메이션 최적화

- 애니메이션은 리플로우와 리페인트를 발생시키는 원인이다. witdh와 같은 크기를 직접적으로 변경하는 애니메이션의 경우 cpu에서 처리하게 되는데 transform의 scale을 활용하여 크기를 변경시키는 경우 gpu에서 처리하게 되므로 성능 향상에 도움이 된다.

6. 웹폰트 경량화

- 사용할 글자만 남겨놓은 서브셋 파일을 활용하여 웹폰트 파일의 크기를 줄인다.

- WOFF2, WOFF와 같은 최적화 폰트를 사용한다.

7. state와 props변경 최소화

- state와 props의 변경을 최소화하여 리렌더링을 최소화한다. 또한 한 컴포넌트에 state를 몰아서 사용하는 경우 state 변화가 빈번하게 발생할 수 있기 때문에 state를 사용하는 컴포넌트 내부에 작성할 수 있도록 한다. 또한 객체 형태의 state의 경우 객체 프로퍼티 중 하나만 사용하는 컴포넌트가 있거나 하는 경우 분리해서 사용하는 것이 좋다.

8. 프롭시 드릴링(props drilling) 피하기

- 부모 컴포넌트에서 자식 컴포넌트로 전달하는 프롭스의 깊이가 깊어질수록 성능에 좋지 않다. 부모의 state가 변경되면 자식 컴포넌트 모두 리렌더링되기 때문이다. 또한 해당 props를 사용하지 않는 컴포넌트를 거치는 경우도 생기며 컴포넌트끼리 결속되어 재사용성이 떨어진다. 개인적으로 2번 이상 넘겨주지 않도록 기준을 정해서 작업하고 있다. 넘어가는 경우 전역 상태 관리 라이브러리를 사용하여 해결할 수 있다.

9. 패키지 정리

- 사용하지 않는 패키지 제거 및 dependencies와 devDependencies를 잘 구분하여 디벨롭 환경에서만 필요한 패키지가 번들에 포함되지 않도록 함

10. 적극적인 캐싱 데이터 사용

- tanstack query와 같은 라이브러리 사용 시 캐싱 데이터를 적극적으로 활용하여 불필요한 리패치를 막는다.

<br>

### # map의 key 사용

- index값은 사용하지 않는다. 만약 배열의 순서가 수정될 경우 중복되는 key값이 발생할 수 있기 때문이다. 그렇기 때문에 유니크한 값을 사용하기 위해 map 메소드를 사용한 배열 요소가 id값을 가지고 있다면 id값을 사용하도록 하고 있다. id값이 존재하지 않다면 가지고 있는 다른 유니크한 값을 사용하거나 배열 요소 자체를 문자열로 변환 후 조합하여 사용하기도 한다.

<br>

### # prop drilling

- prop drilling은 부모 컴포넌트에서 하위 컴포넌트로 props를 전달하는 것을 과정을 말한다. prop drilling이 깊어지게 되면 해당 props의 추적이 어려워져 유지보수가 힘들어지고 실제 props를 사용하는 컴포넌트 사이에 props를 사용하지 않는 컴포넌트도 포함될 수 있다. 또한 부모에 props가 변경되면 하위 컴포넌트들도 모두 리렌더링 되기 때문에 성능 저하에 원인이 될 수 있다. 그렇기 떄문에 prop drilling을 최대한 피해주는 것이 좋은데 prop drilling을 피하는 방법으로는 대표적으로 전역 상태 관리 라이브러리를 사용하거나 컴포넌트를 잘게 쪼개지 않고 가장 가까운 부모 컴포넌트와 props를 공유할 수 있도록 유도하는 것이다.

<br>

### # 얕은 비교(shallow equal) vs 깊은 비교(deep equal)

- 얕은 비교

  얕은 비교는 참조 주소(참조하는 값에 메모리 주소)를 비교한다. react의 경우 state, props, hook의 의존성 배열 값 등은 얕은 비교를 통해 값의 변화를 감지한다.

- 깊은 비교

  참조 주소 및 값까지 비교한다.

<br>

### # 리액트 에러바운더리 컴포넌트와 서스펜스 컴포넌트

- ErrorBoundary 컴포넌트는 자식 컴포넌트의 런타임 시 에러가 발생하는 경우 fallback 속성에 할당한 대체 레이아웃을 제공하기 위해 사용한다. 또한 react query 사용 시 useErrorBoundary 옵션을 true로 설정하여 isError를 대체할 수 있다. 또 ErrorBoundary는 Suspense와 함께 많이 사용된다. Suspense 컴포넌트는 자식 컴포넌트의 렌더링 지연 시 fallback 속성에 할당한 대체 레이아웃을 제공하기 위해 사용한다. React.lazy와 함께 코드스플리팅을 위해서도 사용된다. 또한 ErrorBoundary와 마찬가지로 react query와 함께 사용할 수 있다. useQuery에 suspence 옵션을 true로 설정하여 isLoading을 대체할 수 있다. nextjs에서는 Suspense 컴포넌트를 loading 파일, ErrorBoundary 컴포넌트를 error 파일로 대체해서 사용할 수 있다.

<br>

### # Client Side Routing

- 라우팅은 사용자가 웹사이트 내에서 페이지를 이동하는 과정이다. 서버 사이드 라우팅의 경우 페이지 이동 시 모든 데이터를 새로 요청하게 되어 화면 깜빡임이 발생한다. 반면 클라이언트 사이드 라우팅은 실제 페이지를 전환하는 것이 아닌 Javascript를 통해 페이지를 전환하고 필요한 데이터만 추가로 요청하기 때문에 라우팅 속도도 빠르고 화면 깜빡임이 발생하지 않는다. react와 마찬가지로 nextjs에서도 Link 컴포넌트를 사용하면 클라이언트 사이드 라우팅을 할 수 있다. 반면 a 태그를 사용하면 서버 사이드 라우팅한다. (예시: 리액트 라우터는 클라이언트 사이드 라우팅)

<br>

### # react-query (tanstack query)

- react-query란?

  react-query 라이브러리는 비동기 통신을 편리하게 하기 위한 라이브러리이다. react-query의 useQuery를 통해 받아온 데이터는 캐싱할 수 있고 캐싱 된 데이터는 key값을 통해 컴포넌트 간 공유하여 API 호출을 최적화할 수 있다. 또한 useQuery가 반환하는 data, isLoading, isError 등을 통해 데이터나 예외 처리를 쉽게 할 수 있으며 retry와 같은 옵션을 사용하여 요청 실패 시 재요청을 시도할 수 있고, enable과 같은 옵션을 활용하여 조건이 부합하는 경우에만 API를 호출할 수 있고, staleTime이나 cacheTime과 같은 옵션을 활용하여 캐싱 데이터의 최신화를 관리할 수 있다는 장점이 있다. 또한 이 외에도 onSuccess, onError, onSettled(온새틀리드)를 통해 요청 상태에 따른 추가적인 후속 처리를 할 수도 있다. 또한 데이터 조회 시 useQuery를 사용하였다면 데이터 추가, 갱신, 삭제 시에는 useMutation을 사용한다. useMutation가 반환하는 mutate를 통해 API를 호출할 수 있다.

  ```jsx
  // useQuery 예시
  const Todos = () => {
    const { isLoading, isError, data, error } = useQuery(
      "todos",
      fetchTodoList,
      {
        staleTime: 2 * 60 * 1000,
        cacheTime: Infinity,
        retry: 0,
        onSuccess: (data) => {
          console.log(data);
        },
        onError: (error) => {
          console.log(error.message);
        },
      }
    );

    if (isLoading) {
      return <span>Loading...</span>;
    }

    if (isError) {
      return <span>Error: {error.message}</span>;
    }

    return (
      <ul>
        {data.map((todo) => (
          <li key={todo.id}>{todo.title}</li>
        ))}
      </ul>
    );
  };
  ```

  ```jsx
  // useMutation 예시
  function App() {
    const fetchAdd = async (info) => {
      const { data } = await axios.post(`/add`, info);

      return data;
    };

    const { mutate, isLoading, isSuccess, isError } = useMutation(fetchAdd, {
      onMutate: (variables) => {
        // variables : {id: 1}
        console.log("onMutate", variables);
      },
      onError: (error, variables, context) => {
        // error
      },
      onSuccess: (data, variables, context) => {
        console.log("success", data, variables, context);
      },
      onSettled: (data, error, variables, context) => {
        // end
      },
    });

    const handleSubmit = () => {
      // onMutate 실행 => 성공시 onSuccess 실행 => 끝나면 onSettled 실행
      mutate({ id: 1 });
    };
  }
  export default App;
  ```

- staleTime (리패치 관련, 최신화 관련)

  데이터가 fresh 상태로 유지되는 시간을 지정한다. fresh 상태일 때는 해당 데이터를 재요청하지 않는다. stale 상태가 되는 경우 캐싱 데이터와 무관하게 재요청하여 최신 데이터 상태를 유지하도록 한다.

- cacheTime (메모리에 캐시 유지 시간)

  데이터가 캐싱되는 시간을 결정한다. 해당 시간이 지나면 가비지 콜렉터로 수집되어 사용할 수 없게 된다. 나같은 경우 보통 cacheTime을 Infinity로 설정하고 staleTime을 설정하여 캐싱 데이터를 업데이트하였다.

- enable

  enable 내부에 삼항연산자나 조건을 할당하여 조건에 맞는 시기에 호출할 수 있다.

<br>

### # 동적 라우팅

- react-router-dom에 Route 컴포넌트에 path 경로를 콜론 뒤에 변수로 지정하고 아이템 리스트에서 리스트 클릭 시 해당 아이템에 유니크한 id값을 path 경로로 지정해주어 동적 라우팅을 구현하였다. nextjs는 동적 라우팅을 적용할 파일 네임을 대괄호로 지정하여 구현할 수 있다.

  ```jsx
  // Router.js
  <Route path="/productDetail/:id" element={<ProductDetail />} />;

  // ProductList.js
  const goToDetail = (productId) => {
    navigate(`/productDetail/${productId}`);
  };
  ```

<br>

### # 페이지 네이션 구현 방법

- 한 페이지에 보여 줄 데이터 수, 페이지 넘버 등의 정보가 담겨있는 쿼리 스트링을 백엔드와 지정하여 맞춘 뒤 url에 useSearchParams와 같은 hook을 이용하여 url에 백엔드와 맞춘 쿼리 스트링이 포함되도록 지정하고 이전 페이지나 다음 페이지로 이동 시 url의 포함 된 쿼리 스트링을 useLocation과 같은 hook으로 가져온 뒤 location에 search key에 접근하여 해당 데이터를 요청하면 페이지 네이션을 구현할 수 있을 것 같다.

<br>

### # 디자인 패턴 (https://velog.io/@iamjoo/mvc-mvp-mvvm-flux-%EB%94%94%EC%9E%90%EC%9D%B8-%ED%8C%A8%ED%84%B4-86ocg4bf)

- MVC 패턴

  - 구조

    1. 모델 : 데이터 처리 담당

    2. 뷰 : 화면 처리 담당

    3. 컨트롤러 : 사용자의 입력을 받고 모델과 뷰에 중간 역할

  - 동작

    ![mvc](https://user-images.githubusercontent.com/85284246/178215067-a4f2ddbe-0f4a-41be-9683-e22f62d37771.png)

    1. 사용자의 액션들은 컨트롤러에 들어오게 된다.

    2. 컨트롤러는 사용자의 액션을 확인하고, 모델을 업데이트한다.

    3. 컨트롤러는 모델을 나타내줄 뷰를 선택한다.

    4. 선택 된 뷰는 업데이트 된 모델을 이용하여 화면을 나타낸다.

  - 장점 : 패턴의 사용이 단순하다.

  - 단점 : 뷰와 모델 사이의 의존성이 높다. 높은 의존성 때문에 어플리케이션이 커질수록 복잡하지고 유지보수가 어렵게 만들 수 있다.

<br>

- MVP 패턴

  - 구조

    1. 모델 : 데이터 처리 담당

    2. 뷰 : 사용자로부터의 입력을 받고, 화면 처리 담당

    3. 프레젠터 : 뷰와 모델 사이에 자료 전달 역할

  - 동작

    ![mvp](https://user-images.githubusercontent.com/85284246/178215069-6c1d8fb3-201e-4d31-b138-b4b1457cca66.png)

    1. 사용자의 액션들은 뷰를 통해 들어오게 된다.

    2. 뷰는 데이터를 프레젠터에 요청한다. 이 때 관계는 1대1 관계이다.

    3. 프레젠터는 모델에게 뷰 업데이트에 필요한 데이터를 요청한다.

    4. 모델은 프레젠터에게 요청받은 데이터를 응답한다.

    5. 프레젠터는 뷰에게 데이터를 응답한다.

    6. 뷰는 프레젠터가 응답한 데이터를 이용하여 화면을 나타낸다.

  - 장점 : 프레젠터를 통해서만 데이터를 전달 받기 때문에 뷰와 모델의 의존성이 없다.

  - 단점 : 뷰와 프레젠터 사이의 의존성이 높다.

<br>

- MVVM 패턴

  - 구조

    1. 모델 : 데이터 처리 담당

    2. 뷰 : 사용자로부터의 입력을 받고, 화면 처리 담당

    3. 뷰모델: 뷰와 모델 사이에 매개체 역할

  - 동작

    ![mvvm](https://user-images.githubusercontent.com/85284246/178215072-2a197512-1d58-458d-8bef-3893678a5bef.png)

    1. 사용자의 액션들은 뷰를 통해 들어오게 된다.

    2. 뷰는 데이터를 뷰모델에 요청한다.

    3. 뷰모델은 모델에게 뷰 업데이트에 필요한 데이터를 요청한다.

    4. 모델은 뷰모델에게 요청받은 데이터를 응답한다.

    5. 뷰는 뷰모델과의 데이터 바인딩(데이터를 묶어 동기화시킨다)을 이용해 화면을 갱신한다.

  - 장점 : 뷰와 모델 사이의 의존성이 없고 뷰모델은 모델하고만 소통을 하고 데이터만 관리하는 방식으로 뷰와의 의존성을 없앴다.

  - 단점 : 뷰모델의 설계가 어렵다.

<br>

- FLUX 패턴 : FLUX패턴은 MVC 패턴의 단점을 개선하고자 등장했다. 페이스북에서는 뷰에서 사용자 입력을 받아 모델과 뷰 사이에 양방향 데이터 흐름을 가지도록 만들었는데 애플리케이션의 규모가 커질수록 데이터 흐름을 파악하기가 어렵고 복잡도가 증가하여 예상치 못한 에러가 발생한다는 문제가 있었다. 그래서 나온 것이 FLUX 패턴이다. FLUX패턴은 항상 디스패치, 스토어, 뷰, 액션으로 데이터가 전달되며 액션을 통해 다시 디스패치로 데이터가 전달되는 단방향 데이터 흐름을 가지고 있다. 또한 FLUX 패턴의 일부분을 적용시킨 것이 전역 상태 관리 라이브러리인 리덕스와 몹엑스이다.

  - 구조와 동작순서 : 액션, 디스패처, 스토어, 뷰(컨트롤러 뷰)

    ![flux](https://user-images.githubusercontent.com/85284246/178215058-06245ee4-fa91-46ce-9497-c21dc423131b.png)

    1. 액션 : 액션 생성자를 통해 디스패처에게 액션 객체를 전달한다.

    2. 디스패처 : 액션 객체를 받아 액션 객체의 타입을 정의하여 스토어에 전달한다.

    3. 스토어 : 액션 객체 타입을 받아 참고하여 상태를 업데이트 시키고 상태를 저장한다.

    4. 뷰 : 컨트롤러 뷰는 스토어의 상태 변경 시 스토어의 데이터를 가져와 자식 뷰에게 분배한다.

  - 장점 : 단방향 데이터 흐름으로 데이터 흐름을 파악하기 쉽기 때문에 예상하지 못한 에러를 방지할 수 있다.

  - 단점 : FLUX 패턴을 적용한 라이브러리는 비교적 러닝 커브가 높은 편이다.

- Atomic 패턴 : 텍스트나 버튼처럼 가장 작은 단위의 컴포넌트인 Atom 부터 Molecule, Organism, Template, Page 단위로 컴포넌트를 구분, 이때 Page 단위 컴포넌트에서는 데이터의 패칭 및 가공을 담당하고 그 하위 단위의 컴포넌트들은 뷰만을 책임지는 프레젠테이셔널 컴포넌트로 분리함으로써 컨테이너와 프레젠테이셔널 컴포넌트의 역할을 명확하게 구분 (루머에서 지금예약 운영 시 사용했던 디자인 패턴)

- react 패턴 (Presentational and Container Pattern) : 기능만을 담는 컴포넌트와, 뷰만을 담는 컴포넌트로 분리하는 패턴이다. 담당하는 기능이 분리되어 있기 때문에 가독성이 높고, 유지보수가 쉽고 재사용성이 뛰어나다. 또 같은 state를 다른 container에게 props 내림으로 상태를 공유 할 수 있다.

  - 프레젠테이셔널 컴포넌트(present component)

    뷰를 담는 컴포넌트이다. 상태가 없는 컴포넌트(stateless component)라고도 불린다. state를 직접 조작하지 않으며, 컨테이너 컴포넌트가 내려준 props를 사용한다. state 관련 훅을 사용하지 않고 state를 거의 가지지 않으며 만약 state를 가지고 있다면 데이터에 관한것이 아닌 ui 상태에 관한 state를 가지고 있다.

  - 컨테이너 컴포넌트(container component)

    기능을 담는 컴포넌트이다. 상태가 있는 컴포넌트(stateful component)라고도 불린다. 어떤 동작을 하고 어떤 로직을 수행하는지와 관련이 있다. 마크업을 하지 않고 스타일을 사용하지 않는다. 데이터와 데이터 조작에 관한 함수를 만들고 프레젠테이셔널 컴포넌트에 제공한다.

- 합성 컴포넌트 패턴 : 컴포넌트를 기능별로 나누어 합성(Composition)으로 조립, 반복되는 로직은 커스텀 훅으로 추출, 즉 한 컴포넌트 내에서 해당 컴포넌트에 종속되는 여러 컴포넌트들을 만들어 외부에서 조합해서 사용

- 기능기반 구조 패턴(Feature-based Folder Structure) : 기능 단위(페이지나 도메인)로 폴더를 나누는 방식, 즉, 프로젝트를 특정 기능을 기준으로 디렉토리를 나누고, 그 하위에 해당 기능에 관련된 모든 파일을 배치함.

<br>

### # 웹사이트 scrolling 성능을 향상 방법

- 스크롤 이벤트의 특성 상 반복적으로 이벤트를 호출되게 되는데 스크롤 이벤트와 같이 반복적으로 호출되는 이벤트는 사용하지 않는 이벤트를 제거(실행 중지)하기 위해 클린업 함수를 적용시켜야한다. 만약 스크롤 이벤트에서 클린업 함수로 처리를 하지 않는 경우 모든 이벤트가 실행되거나 메모리에서 제거되지 않기 때문에 성능 이슈가 발생한다. removeEventListener를 통해 클린업 함수를 만들어 클리어 처리를 해주어야 메모리 누수가 발생하지 않는다. 또한 스크롤 이벤트의 경우 쓰로틀링을 구현하여 일정 시간동안 한번만 실행되도록 구현할 수 있다. 쓰로틀링은 로대쉬(Lodash)라이브러리의 쓰로틀(throttle)로 구현하거나 직접 구현할 수 있다. 쓰로틀링 구현은 직접 구현할 경우 setTimeout을 통해 일정 시간동안 스크롤 이벤트를 실행시키고 쓰로틀링을 체크하는 boolean타입의 state를 함께 사용하여 구현할 수 있다. 또한 추가로 스크를 되는 컨텐츠 중 사용자가 보는 뷰포트 영역의 컨텐츠만 렌더링하기 위해 windowing 기법을 적용할 수 있다. windowing 기법을 편리하게 적용시키기 위한 react 라이브러리로는 react-window와 react-virtualized가 있다.

```javascript
// 클리어 처리 예시
// useEffect 는 deps 배열의 내용이 변경될 때마다 함수를 호출하고, 그 만큼 addEventListener 가 호출되면서 브라우저가 호출해야하는 함수의 갯수도 늘어난다. 아래 코드는 value 가 변경될 때마다 addEventListener 로 새로운 함수를 입력하고 있다. value 가 1 => 2 => 3 순서로 변경됐다고 가정하면 스크롤 시 우리가 원하는 결과는 콘솔 로그에 3이 출력되는 것일 텐데 하지만 removeEventListener 를 호출하지 않아서 1, 2, 3 이 각각 출력될 것이다. 만약 아래 코드에서 주석을 제거하고 클리어 처리를 하는 경우 3이 출력된다.

useEffect(() => {
  window.addEventListener("scroll", () => console.log(value));

  // return () => {
  //   window.removeEventListener("scroll", () => console.log(value));
  // };
}, [value]);
```

<br>

### # 지연 로딩(Lazy Loading)

- 지연 로딩(Lazy Loading)

  레이지 로딩은 말 그대로 지연 로딩을 말한다. 사용자가 실제로 해당 리소스를 필요로 할 때까지 다운로드를 지연시키는 기법이다. 예를 들어 사용자가 웹 사이트를 접속할 때 CSR에서는 메인 번들을 통째로 로드하게 된다. 이때 사용자가 다른 페이지에 접근하지 않으면 다른 페이지의 코드는 메인 번들에 포함될 필요가 없다.

  이런 경우 라우트 레벨에서 suspense 컴포넌트와 함께 react.lazy(next에서는 next/dynamic의 dynamic)를 활용하여 코드 스플리팅 한 후 레이지 로딩하는 방식으로 사용자가 해당 페이지에 접근할 때 쪼개진 번들을 지연 로드할 수 있게 한다. 또한 이 외에도 모달과 같은 조건부 렌더링에도 지연 로딩을 적용할 수 있다.

  또한 스크롤이 긴 페이지에서 사용자가 모든 컨텐츠를 보지 않고 나가는 경우 리소스 낭비가 발생할 수 있다. 이럴 때는 뷰포트를 관찰하여 레이지 로딩을 적용 시킬 수 있다. Intersection Observer 혹은 scroll 이벤트를 통해 컨텐츠가 뷰포트 내에 포함되는 경우 로드되도록 구현할 수 있다.

  이렇게 레이지 로딩을 적용하여 렌더링 최적화 및 리소스 낭비를 막을 수 있다.

- 요약

  - CSR에서 사용자가 다른 페이지를 사용하지 않을 때 라우트 레벨에서 코드 스플리팅하여 레이지 로딩

  - 모달과 같은 조건부 렌더링에서 지연 로딩

  - 스크롤이 긴 페이지에서 Intersection Observer 혹은 스크롤 이벤트를 활용하여 뷰포트 감지 후 레이지 로딩

  ```jsx
  // 라우트 레벨에서 코드 스플리팅
  import React, { Suspense, lazy } from "react";
  import { BrowserRouter as Router, Route, Switch } from "react-router-dom";

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

<br>

### # 트래픽 및 트래픽 초과 대응

- 트래픽이란?

  트래픽은 네트워크 상에서 일정 시간 동안 흐르는 데이터 양(즉, 데이터 전송량)이나, 사용자 요청 수 등을 의미한다.

- 트래픽 초과 대응

  - CDN, 로드 밸런서 등을 통한 트래픽 분산

  - 클라이언트 단에서는 이미지, 스크립트 등 리소스 크기를 최적화해서 전송 데이터량 줄이기 (ex 코드 스플리팅, 레이지 로딩)

  - AWS와 같은 확장성이 좋은 클라우드 컴퓨팅을 활용하여 유연한 서버 확장

  (참고 사항 : CDN과 로드 밸런서는 기본적으로 다른 유형의 도구이다. CDN의 주요 목적은 넓은 지리적 영역에 컨텐츠를 분산시켜 물리적으로 가까운 서버에 요청을 하는 방식이고, 로드 밸런서의 주요 목적은 트래픽 분산을 위해 서버를 분산하는 것을 말한다.)

<br>

### # 프로젝트를 하면서 메모리 누수(leak) 이슈가 있었는지?

- useEffect를 사용하여 api를 요청하고 응답에 따라 state를 업데이트 시킬 때 api 요청 후 서버에서 응답이 지연되는 경우 응답을 받기 전 해당 컴포넌트가 언마운트되면 api 호출 완료 후 state 업데이트 시도 시 메모리 누수가 발생한다. 즉 이전 컴포넌트에서 작업이 완료되기 전 컴포넌트가 언마운트 되는 경우 메모리 누수가 발생하는 것이다. 클린업 함수를 통해 컴포넌트가 언마운트 될 때 해당 작업을 종료하는 방식으로 문제를 해결할 수 있다. 또한 이미지 미리보기 구현 시 URL.createObjectURL을 통해 이미지 미리보기를 구현하였는데 해당 URL은 생성한 페이지에서만 유효하고 문서가 닫히거나 페이지를 이동하는 경우 유효하지 않기 때문에 메모리 누수가 발생한다. 이 때 URL.revokeObjectURL을 통해 생성한 객체 URL을 메모리에서 제거해주어야한다.

<br>

### # Webpack

- 웹팩

  최신 프론트엔드 프레임워크에서 가장 많이 사용되는 모듈 번들러이다. 모듈 번들러란 웹 애플리케이션을 구성하는 자원(HTML, CSS, Javscript, Images 등)을 모두 각각의 모듈로 보고 이를 압축하고 병합해서 하나의 번들 파일을 만드는 도구를 의미한다. 또한 모듈 번들러의 종류로는 웹팩 이 외에도 rollup, vite, esbuild 등이 있다. 모듈 시스템의 한계로 인해 등장하게 되었다.

- 웹팩 사용 이유

  웹 페이지를 구성하기 위해 HTTP 요청으로 html, css, js, 이미지, 웹 폰트, json 데이터 등 많은 파일을 받아오게 되는데 받아오는 파일이 많을수록 HTTP 요청이 많아지고 주로 사용하는 HTTP 1.1에서는 하나의 커넥션에서 하나의 요청(파이프라이닝 기술로 동시 최대 6개 요청)이 끝난 후 다음 요청을 보낼 수 있으므로 HTTP 요청이 많아지면 성능 저하가 발생할 수 있다. 이런 경우 웹팩을 통해 js, css, 이미지 등을 하나로 압축하여 번들 파일을 만들어 파일의 크기를 줄이고 HTTP 요청 횟수를 줄일 수 있다. 즉 웹팩을 사용하면 html, css, js 등의 모듈화와 코드 축소, 이미지 압축으로 인한 네트워크 비용 감소 및 요청 회수 감소 등에 장점이 있다.

  웹팩을 사용하지 않았을 경우 발생하는 문제에 대해 더 자세한 예시를 보자. 과거 ES6 모듈 시스템이 등장하기 전에는 a.js, b.js, c,js의 각 javasciprt 파일이 있다고 했을 때 이 javascript 파일들을 각 script 태그로 나누어 모듈처럼 사용하였다. 하지만 이러한 경우 전역을 공유하는 문제가 발생하였다.

  이러한 문제를 해결하기 위해 ES6 모듈 시스템이 등장하였다. ES6 모듈 시스템을 적용하는 경우 위와 같이 script 태그로 나뉘는 것이 아닌 하나의 script 태그 내부에서 a.js, b.js, c,js의 각 javasciprt 파일을 import문을 통해 가져오는 구조가 된다. 그렇게 되면 javascript 파일들은 각각의 모듈이 되는 것이다. 하지만 이 경우에도 문제가 발생한다. 해당 프로젝트의 구조 전체를 정적으로 배포한다고 했을 때 모듈로 나뉘어진 javascript 파일을 각각 요청해서 받아오게 된다. 이로 인해 네트워크 요청이 많아져 퍼포먼스가 떨어지는 문제가 발생하게 된다.

  그러면 여기서 생기는 의문이 하나의 javascript 파일에 모든 코드를 작성하면 되지 않느냐는 의문이 생길 수 있다. 이런 방식은 과거 ES6 모듈 시스템이 추가된 이유를 생각해보면 된다. 만약 하나의 javascript에 모든 javascript를 작성한다면 파일 크기가 매우 커지고 유지 보수가 어려워지며 코드 재사용 또한 어려워지는 문제가 발생할 수 있다.

  이와 같은 문제들로 인해 웹팩이나 vite 같은 번들러는 필수적으로 사용해야한다.

- 웹팩의 기본 옵션

  - Entry

    앱이 번들 처리를 시작할 지점. index.js부터 시작해서 import문을 따라서 빌드를 진행. 여러 개 지정해서 코드 스플리팅 할 수도 있음

  - Output

    - output.path

      빌드된 파일이 디스크에 저장될 물리 경로 (Node.js 기준)

    - output.filename

      빌드 결과물 파일 이름

    - output.publicPath

      브라우저가 정적 파일을 불러올 때 사용되는 base URL 경로 (HTML, JS 내 동적 로딩 등에서 사용), prefix와 같이 동작한다.

      ```js
      // publicPath: '/static/';
      <script src="/static/bundle.js"></script>
      ```

  - resolve

    resolve 옵션은 모듈을 import하거나 require할 때 Webpack이 해당 모듈의 위치를 어떻게 찾을지 결정하는 설정이다. 즉, 파일을 찾는 규칙, 확장자, 별칭(alias) 등을 지정해서 모듈 경로 해석을 커스터마이징할 수 있다.

    - resolve.extensions

      import 시 확장자를 생략할 수 있게 한다.

      ```js
      // webpack 설정
      resolve: {
        extensions: [".js", ".jsx"];
      }

      // 위 설정이 있는 경우
      import App from "./App"; // 실제는 ./App.js 또는 ./App.jsx
      ```

    - resolve.alias

      긴 경로를 짧고 의미 있는 이름으로 치환할 수 있게 한다.

      ```js
      // webpack 설정
      alias: {
        '@utils': path.resolve(__dirname, 'src/utils')
      }

      // 위 설정이 있는 경우
      import { formatDate } from '@utils/date';
      ```

    - resolve.modules

      Webpack이 모듈을 찾을 디렉토리 목록을 지정

      ```js
      // webpack 설정
      // 기본값은 ['node_modules']. 아래처럼 설정하면, import X from 'myLib' 시 src/ 폴더부터 먼저 찾는다.
      modules: ["src", "node_modules"];
      ```

    - resolve.mainFiles

      디렉토리를 import할 경우 찾을 기본 파일 이름을 지정

      ```js
      // webpack 설정
      // import Foo from './foo'일 때, 실제로는 ./foo/index.js 또는 ./foo/main.js가 된다.
      mainFiles: ["index", "main"];
      ```

  - loader

    기본적으로 Webpack은 Javascript(`.js`) 및 JSON(`.json`) 파일만 해석 가능하다. 하지만 loader를 사용하면 다른 포멧의 파일들(예: TypeScript, SCSS, 이미지 등)을 처리하고 JavaScript 모듈로 변환할 수 있다. 즉 그 외 파일들은 loader가 있어야 import 가능하다.

    ```js
    // 웹팩 설정 예시
    module: {
      rules: [
        {
          test: /\.tsx?$/, // .ts, .tsx 파일을
          use: "ts-loader", // ts-loader로 처리
          exclude: /node_modules/, // node_modules는 제외
        },
      ];
    }
    ```

    ```js
    // use 배열 예시 (체이닝), 아래처럼 순서는 오른쪽 → 왼쪽 (아래 → 위) 로 적용
    module: {
      rules: [
        {
          test: /\.scss$/,
          use: [
            "style-loader", // 3. 스타일을 <style> 태그로 삽입
            "css-loader", // 2. CSS 파일을 JS 모듈로 변환
            "sass-loader", // 1. SCSS → CSS 변환
          ],
        },
      ];
    }
    ```

    ```js
    // import 예시
    import "./main.scss"; // SCSS? 브라우저도 JS도 이해 못 함
    import img from "./logo.png"; // PNG도 마찬가지
    ```

    - rules.test

      어떤 파일에 로더를 적용할지 정규식으로 지정

    - rules.use

      어떤 로더를 사용할지 명시 (string 또는 배열 가능)

    - rules.import / exclude

      적용 대상 제외 또는 포함 경로

    - loader 종류

      1. CSS : style-loader + css-loader
      2. File : file-loader, raw-loader, url-loader, asset modules
      3. Typescript : ts-loader, babel-loader + @babel/preset-typescript
      4. Babel : babel-loader

  - plugin

    로더가 파일 단위로 처리한다면, plugin은 주로 빌드 전체 과정에 개입해서 번들된 결과물을 처리한다.

    ```js
    // index.html 파일을 기반으로 자동으로 <script src="bundle.js">를 삽입한 HTML 파일을 생성하는 코드
    const HtmlWebpackPlugin = require("html-webpack-plugin");

    module.exports = {
      plugins: [
        new HtmlWebpackPlugin({
          template: "./public/index.html",
        }),
      ],
    };
    ```

    - plugin 종류

      1. HtmlWebpackPlugin : HTML 파일 자동 생성 및 번들 삽입
      2. DefinePlugin : 전역 상수 정의 (예: process.env.NODE_ENV)
      3. MiniCssExtractPlugin : CSS를 별도 파일로 분리
      4. CleanWebpackPlugin : 빌드 전에 dist 폴더 정리
      5. BundleAnalyzerPlugin : 번들 사이즈 시각화
      6. CopyWebpackPlugin : 정적 파일 복사 (예: public/assets 등)

  - externals

    externals 옵션은 특정 모듈을 번들에서 제외하고 외부에서(예: CDN, 전역 변수 등) 참조하도록 설정하는 기능이다. 즉, Webpack이 그 모듈을 직접 번들에 포함하지 않도록 하여 번들 사이즈를 줄이고 로딩 속도를 높일 수 있게 한다. 예를 들어 우리 코드가 의존하고 있지만 빌드 과정에는 포함하지 않아도 되는 axios, jQuery 같은 써드파티 라이브러리를 이 externals에 명시하면 빌드 프로세스에 포함되지 않는다. 단, 제외된 모듈은 HTML에서 `<script>` 태그 등을 통해 직접 로딩해야 하며, 그렇지 않으면 런타임 오류가 발생한다.

    ```js
    // axios와 같은 써드파티 라이브러리는 패키지로 제공될때 이미 빌드 과정을 거쳤기 때문에 빌드 프로세스에서 제외하는 것이 좋다.
    // axios는 이미 node_modules에 위치해 있기 때문에 이를 웹팩 아웃풋 폴더에 옮기고 index.html에서 로딩해야한다.
    // 파일을 복사하는 CopyWebpackPlugin을 설치한다. 플러그인을 사용해서 라이브러리를 복사한다.
    const CopyPlugin = require("copy-webpack-plugin");

    module.exports = {
      plugins: [
        new CopyPlugin([
          {
            from: "./node_modules/axios/dist/axios.min.js",
            to: "./axios.min.js", // 목적지 파일에 들어간다
          },
        ]),
      ],
    };
    ```

    ```html
    <!-- index.html에서는 axios를 로딩하는 코드를 추가한다. -->
    <!-- src/index.html -->
    <html>
      <body>
        ...
        <script type="text/javascript" src="axios.min.js"></script>
      </body>
    </html>
    ```

  - performance

    번들 크기와 관련된 경고 메시지를 제어하는 설정이다. 이 설정은 실제 성능 최적화를 수행하지는 않지만, 큰 파일이 감지될 때 개발자에게 경고를 줘서 문제를 인식하게 해주는 용도이다.

    ```js
    performance: {
      hints: 'warning',            // 'warning' | 'error' | false
      maxEntrypointSize: 512000,   // entry point(예: main.js)의 최대 크기 (bytes), 512000 -> 약 500KB
      maxAssetSize: 244000,        // 개별 에셋의 최대 크기 (bytes)
    }
    ```

- 웹팩 최적화

  - 번들 사이즈를 줄여야 하는 이유

    1. 네트워크 비용 : 파일 용량이 클수록 네트워크 통신이 더 오래 걸린다.

    2. 파싱 및 컴파일 비용 : 브라우저에서 javascript 파일의 크기가 큰 경우 파싱 및 컴파일 하는데 시간이 오래 걸리고 하이드레이션이 지연되어 사용자 상호 작용이 지연될 수 있다.

    3. 메모리 비용 : 실행되지 않는 JS도 브라우저 메모리에 올라가 RAM을 차지하여 메모리를 낭비하게 된다.

  - 번들 사이즈 줄이기

    - webpack mode

      1. development

      강력한 소스 매핑, 로컬 호스트 서버에서는 라이브 리로딩이나 핫 모듈 리플레이스먼트 기능을 목적으로 이용한다.

      2. production

      기본 값이다. 로드 시간을 줄이기 위해 번들 최소화, 가벼운 소스맵 및 에셋 최적화에 초점을 맞춘다.

    - source map

      source map은 번들된 파일과 원본 소스 파일을 매핑해주는 파일이다. source map이 있으면, 브라우저 개발자 도구는 이걸 원래 코드로 되돌려 보여줄 수 있다. development mode에서는 eval, production mode에서는 source-map이 적절하다.

      1. eval : 빌드, 리빌드가 가장 빠름, 개발용. 소스 맵이 코드 안에 포함됨
      2. source-map : 완전한 맵 생성, 배포용 디버깅 가능
      3. cheap-module-source-map : 빠르면서 어느 정도 디버깅 가능
      4. hidden-source-map : 맵은 생성되지만 브라우저에선 안 보임 (오류 추적용)
      5. nosources-source-map : 맵은 있지만 원본 코드는 안 보임 (보안 목적)

      ```js
      module.exports = {
        devtool: "source-map", // 또는 'eval', 'cheap-module-source-map', 등
      };
      ```

    - code splitting

      하나의 번들을 여러 개의 청크로 나누는 기법을 말한다. 나누어진 청크는 필요한 상황에 로드하여 초기 로드 시간을 단축 시킬 수 있다.

      1. entry에 entry-point를 지정하여 나누는 기법

      entry point를 직접 지정하여 그것을 기준으로 번들을 나눌 수 있다. key는 번들 이름, value는 경로가 된다.

      ```js
      // webpack.config.js
      module.exports = {
        entry: {
          home: "./src/home.js",
          about: "./src/about.js",
        },
        output: {
          filename: "[name].bundle.js", // → 하나의 bundle.js가 home.bundle.js, about.bundle.js로 쪼개짐
          path: __dirname + "/dist",
        },
      };
      ```

      2. dynamic import

      dynamic import를 통해 불러오는 기법, preload 및 prefetch도 지원한다. preload는 곧바로 사용될 가능성이 높은 글꼴 등, prefetch는 추후에 사용될 가능성이 높은 모달 등에 사용할 수 있다.

      ```js
      // dynamic import
      if(true){
        import("./Modal.js").then(() => { ... })
      }

      // SPA에서 동적으로 컴포넌트를 불러오기 위해서는 Suspense와 lazy를 사용해야함.
      const Modal = React.lazy(() => import("./Modal"));

      // preload 및 prefetch
      import(/* webpackPrefetch: true */ "./MyComponent");
      import(/* webpackPreload: true */ "./MyComponent");
      ```

      3. optimization.splitChunks 사용

      splitChunks을 사용하면 vendor.bundle.js에 React 등 라이브러리를 별도 번들로 분리하여 중복 번들 생성을 방지할 수 있다.

      ```js
      module.exports = {
        optimization: {
          splitChunks: {
            chunks: "all", // 모든 종류의 import에 대해 분할 수행
          },
        },
      };
      ```

    - tree shaking

      사용하지 않는(dead) 코드를 최종 번들에서 제거하여 번들 사이즈를 최적화하는 기법이다. ES Modules (ESM, import / export)을 사용할 때 작동한다. Commonjs를 사용하는 경우에는 적용되지 않는다.

      sideEffects는 import하는 것만으로도 외부에 영향을 끼치는 코드임을 의미한다. (ex polyfill) 즉 sideEffects가 있는 경우 tree shaking이 불가하다. 그렇기 때문에 package.json에 모든 모듈이 sideEffects가 없음을 의미하는 false를 지정하거나 개별로 지정해야한다. 예시로 사용하는 라이브러리의 package.json을 확인해보면 대부분 sideEffects가 false인 것을 확인해볼 수 있다.

      추가로 utils.js와 같이 한 파일 안에 여러 개의 export를 만드는 경우 tree shaking이 제대로 적용되지 않을 수 있는데 해당 파일 내부에서 다른 곳에 사용될 수 있기 때문이다. 그렇기 때문에 하나의 파일에서는 하나의 export가 있는 것이 tree shaking에 좋다. -> 검증 필요

      ```js
      // tree shaking 예시
      // utils.js
      export function add(a, b) {
        return a + b;
      }

      export function subtract(a, b) {
        return a - b;
      }

      // main.js
      // 이 경우 subtract는 실제로 사용되지 않았으므로 Webpack은 최종 번들에서 사용되지 않은 export인 subtract를 자동으로 제거
      import { add } from "./utils";

      console.log(add(1, 2));
      ```

      ```js
      // sideEffects 예시
      // package.json
      {
        "sideEffects": ["*.css"]
      }
      ```

  - 빌드 속도 줄이기

    - persistent cache

      빌드 결과를 메모리 혹은 하드 디스크에 저장하여 리빌드 시 변화가 없다면 캐시된 빌드 결과물을 재활용하여 빌드 속도를 높인다. 기본 값은 memory 이다. 빌드 결과물 재사용 여부는 snapshot을 통해 결정한다.

      ```js
      module.exports = {
        cache: {
          type: "filesystem", // 디스크 (HDD/SSD 등 로컬 파일시스템)에 캐시를 저장
          buildDependencies: {
            // 캐시 무효화 기준: webpack 설정 파일이 바뀌면 캐시 무효화
            config: [__filename],
          },
        },
      };
      ```

    - snapshot

      파일 시스템의 상태를 추적해서 재빌드 여부를 결정하는 캐시 메커니즘의 일부이다. 이 파일이 바뀌었는지 확인하는 기준 정보(스냅샷)를 저장해두고 다음 빌드 시 비교해서 바뀌었으면 캐시를 무효화하여 다시 빌드하고 안 바뀌었으면 캐시를 그대로 사용하는 것이다. 즉 캐시 사용 여부의 기준이 되는 것이다. 캐시 옵션을 켜고 빌드를 하면 `node_modules/.cahce`에 pack 파일이 생성되는데 pack 파일에 붙어있는 정보가 snapshot이다.

      snapshot에는 timestamp와 hash 등에 정보가 있는데 timestamp의 경우 마지막 수정 시간, hash의 경우 파일 content를 hashing 알고리즘을 통해 생성한 string이다. 이 두 가지를 통해 캐시 무효화 여부를 결정할 수 있다. timestamp의 경우 빌드 시 파일의 메타데이터에서 timestamp를 가져와 snapshot의 timestamp와 비교하여 바뀌었다면 캐시를 무효화한다. 다만 속도는 빠르지만 변경없이 저장만 해도 timestamp가 변경되기 때문에 안정성은 떨어진다. 반면 hash의 경우 속도는 상대적으로 느리지만 안정성이 높다. webpack 설정 내부에 boolean 값을 통해 timestamp, hash 중 어떠한 값을 기준으로 캐시 무효화 여부를 결정할지 지정할 수 있다.

      추천하는 설정은 다음과 같다.

      1. 로컬 개발환경에서는 module, buildDependencies, resolve 모두 timestamp true로 하는 것이 좋다. 다만 프로젝트가 큰 경우에는 buildDependencies에 hash true도 추가한다.

      2. CI 빌드시에는 git에서 clone 해오기 때문에 모든 timestamp가 바뀌므로 module, buildDependencies, resolve 모두 hash true로 해주는 것이 좋다.

      3. CI 빌드를 하는데 업데이트만 일어나는 경우, 즉 git pull만 하는 경우에는 module, buildDependencies, resolve 모두 timestamp true, hash true 모두 설정하는 것이 좋다.

      ```js
      module.exports = {
        cache: {
          type: "filesystem",
          buildDependencies: {
            config: [__filename],
          },
        },
        snapshot: {
          module: {
            timestamp: true, // 모듈의 수정 시간 기준으로 캐시 관리
          },
          resolve: {
            timestamp: true, // resolve 경로의 수정 시간 기준으로 캐시 관리
          },
          buildDependencies: {
            config: [__filename, path.resolve(__dirname, "tsconfig.json")], // Webpack 설정이나 빌드 관련 파일이 변경되었을 때 캐시 무효화
          },
          resolveDependencies: {
            timestamp: true, // resolve 경로의 의존성 파일 수정 시간 기준으로 캐시 관리
          },
          managedPaths: [/node_modules/], // node_modules에 이름이 바뀌거나, 버전이 업데이트되는 경우에만 캐시를 무효화
          immutablePaths: [path.resolve(__dirname, "public/assets")],
        },
      };
      ```

<br>

### # Babel

- 바벨

  바벨은 ES6+ 버전 이상의 자바스크립트나 JSX, 타입스크립트 코드를 하위 버전의 자바스크립트 코드로 변환 시켜주는 자바스크립트 트랜스파일러이다. 크로스 브라우징 이슈를 해결하기 위해 사용한다. 즉 최신 JavaScript 문법을 구형 브라우저에서도 동작하게 하기 위해서이다. 브라우저 버전마다 JS 엔진에 버전도 다르다. 그렇기 때문에 브라우저마다 지원하는 JS 문법이 다르다. 또한 React를 예시로 React에서 사용하는 JSX 문법은 브라우저가 이해하지 못한다. 그렇기 떄문에 트랜스파일링을 통해 React.createElement()와 같은 형태로 변환하고 이는 브라우저가 해석할 수 있다. import를 통해 가져온 React 라이브러리의 객체인 React 객체의 메소드가 createElement이고 이 형태는 obj.method()와 같다. 바벨의 빌드 단계는 파싱(바벨 코어가 수행) -> 변환(플러그인이 수행) -> 출력(바벨 코어가 수행) 단계로 이루어지며 Webpack과 같은 정적 모듈 번들러와 함께 사용할 수 있다. (@babel/core, babel-loader, 프리셋 (@babel/preset-env, @babel/preset-react, @babel/preset-typescript 등) 등의 설치)

  ```js
  module.exports = {
    module: {
      rules: [
        {
          test: /\.js$/,
          exclude: /node_modules/,
          use: {
            loader: "babel-loader",
            options: {
              presets: ["@babel/preset-env"], // 👈 필수
            },
          },
        },
      ],
    },
  };
  ```

- 플러그인

  바벨에 파싱, 변환, 출력 빌드 단계 중 변환 단계를 담당하며 어떤 코드를 어떻게 변환할지에 대한 규칙을 정의한다.

- 프리셋

  목적에 맞게 여러 가지 플러그인을 세트로 모아놓은 것이다. 대표 프리셋은 아래와 같다.

  | 프리셋 이름                    | 설명                                                             | 사용 예시               |
  | ------------------------------ | ---------------------------------------------------------------- | ----------------------- |
  | **`@babel/preset-env`**        | 최신 JavaScript 문법(ES6+)을 구형 브라우저에서도 동작하도록 변환 | 일반 JS 프로젝트        |
  | **`@babel/preset-react`**      | JSX 문법을 JavaScript로 변환                                     | React 프로젝트          |
  | **`@babel/preset-typescript`** | TypeScript를 JavaScript로 변환                                   | TypeScript + Babel 조합 |
  | **`@babel/preset-flow`**       | Flow 타입을 제거하고 JS로 변환                                   | Flow 타입 사용 시       |

- 폴리필

  바벨은 ES6 이후 버전을 ES5 버전으로 변환할 수 있는 코드만 변환한다. 만약 최신 기능을 사용하였는데 이 기능이 ES5 버전에는 존재하지 않아 빌드가 누락 된 부분을 폴리필을 통해 변환할 수 있다. 코어제이에스(corejs), 폴리필아이오(polyfill.io) 등이 대표적인 폴리필 패키지이다.

<br>

### # SWC(Speedy Web Compiler)

- SWC(Speedy Web Compiler)란?

  SWC는 컴파일과 번들링 모두를 수행하는 자바스크립트 빌드 툴이다. nextjs에서는 next 12버전부터 바벨 대신 기본 트랜스파일러로 사용되고 있다. 트랜스파일링을 수행했던 바벨과, 코드 경량화를 수행했던 터서(Terser)를 SWC가 대체했다. 싱글 스레드인 자바스크립트로 작성 된 바벨과 테서와는 다르게 SWC는 러스트(Rust)로 작성되어 병렬 처리가 가능하기 때문에 훨씬 빠르다.

- 빌드 시간 측정

  특정 커맨드의 결과가 나오기까지의 시간을 체크해주는 패키지를 사용하여 측정할 수 있다. (ex gnomon)

<br>

### # prettier, eslint, stylelint

- eslint

  자바스크립트 언어와 소스코드를 분석하는 도구로 코드에 특정 스타일과 규칙을 적용해 에러를 찾고 패턴을 적용시킬 수 있는 분석 툴이다. 코드 구현 방식을 지정하여 에러를 사전에 방지하고 코드 퀄리티를 보장하도록 도와준다. 또한 prettier와 같이 코드 스타일과 관련 된 코드 포멧팅도 지원한다. 예를 들면 변수 사용 규칙, 콘솔 사용 방지, 사용되지 않는 객채 등에 경고나 에러를 선택하여 띄워줄 수 있다.

  ```js
  // .eslintrc.json
  {
    "rules": {
      "no-unused-vars": "warn",    // 사용하지 않는 변수 경고
      "no-console": "error"        // console 사용 금지
      "no-var": "warn" // var 사용 시 경고
    }
  }
  ```

- prettier

  prettier는 코드 스타일을 통일되도록 도와주는 코드 포멧터이다. eslint와 같이 코드 구현 방식이 아닌, 줄 바꿈, 공백, 들여 쓰기 등 에디터에서 '텍스트'를 일관되게 작성되도록 도와준다.

  ```json
  // .prettierrc
  {
    "semi": true,
    "singleQuote": true,
    "tabWidth": 2
  }
  ```

  ```js
  // Before
  function hello() {
    console.log("hi");
  }

  // After Prettier
  function hello() {
    console.log("hi");
  }
  ```

- stylelint

  css및 scss를 코드를 분석하는 도구이다. 공백, 따옴표, 들여쓰기와 같이 작성 규칙이나 스타일 순서 등 css의 코드 스타일 규칙을 지정할 수 있다.

  ```json
  // .stylelintrc.json
  {
    "rules": {
      "color-hex-case": "lower", // 16진수 색상 소문자 사용
      "string-quotes": "double", // 문자열은 더블 쿼트 사용
      "indentation": 2 // 들여쓰기 2칸
    }
  }
  ```

<br>

### # 사용자 경험 개선 방법

1. 로딩, 에러, 잘못된 경로 시 대체 페이지 제공

   페이지 로딩 중일 때 로딩 스피너 노출, 에러나 잘못된 경로 시 대체 페이지 제공 등을 통한 사용자 경험향상

2. 스켈레톤 UI 사용

   컨텐츠 로딩 지연 시 사용자의 지루함을 막아주기 위해 로딩 바 혹은 스피너 대신 스켈레톤 UI(대체 UI)를 사용할 수 있다.

3. 비디오 사용 시 대체 이미지

   동영상 사용 시 동영상이 보이지 않는 유저들을 위해 대체 이미지를 깔아준다.

4. 드래그 앤 드롭 기능 시 텍스트 드래그 막기

   드래그 앤 드롭 기능 구현 시 타겟 css에 `use-select: none` 속성을 주어 텍스트가 드래그되는 것을 막을 수 있다.

5. 이미지 태그의 onError 속성

   api로 이미지를 불러와 띄워줄 경우 이미지를 불러오지 못하는 경우(이미지 주소가 N/A로 오는 경우)가 발생할 수 있는데 이 때 이미지 태그의 onError를 사용하여 대체 이미지를 사용하여 에러 처리를 할 수 있다.

6. 쿼리 스트링 활용

   검색 기능 구현 시 쿼리 스트링을 활용하면 사용자가 검색 결과를 다른 사용자들과 공유할 수 있다.

7. 연관 검색어 기능 구현 시 디바운싱 적용

   연관 검색어 기능 구현 시 디바운싱을 적용하여 검색하는 과정 중 원하지 않는 결과물을 노출하지 않도록 함

<br>

### # 패키지 매니저

- npm

  - nodejs의 표준 패키지 매니저로 별도 설치 필요없음

  - 과거 직렬 설치 방식이었으나 현재는 병렬 설치도 지원

  - 과거 보안 이슈가 있었으나 꾸준히 개선 중

- yarn

  - 병렬적 설치로 속도 개선

  - 패키지 캐시 및 재사용 지원

  - 예전엔 npm보다 속도 및 안정성에서 우위였으나 최신 npm 버전과 큰 차이 없음

- yarn berry (Yarn 2 이상의 버전)

  - yarn의 두 번째 버전

  - Plug n Play 방식(node_modules 폴더를 만들지 않고 zip 형태로 패키지를 관리, pnp.cjs 파일에 의존성 매핑 정보를 기록)으로 npm과 yarn에서 발생하는 유령 의존성 문제 해결

  - 패키지 클론 시 install 하지 않아도 되는 제로 인스톨이 가능하기 때문에 CI 단계에서 의존성 설치 시간을 단축시킬 수 있음

- pnpm

  - 글로벌 저장소(캐시)에서 패키지를 관리하여 디스크 공간 절약

  - node_modules를 특이한 방식으로 관리 (hard link) → 중첩 설치 최소화

  - package.json에 명시된 패키지만 글로벌 저장소에서 가져와 설치해 유령 의존성 문제 해결

  - 모노레포 설정이 간단하고 Yarn Berry보다 빠르고 직관적이라는 평가가 많음

- 유령 의존성 : 사용 중인 패키지에 의존성 패키지, 즉 개발자가 직접 사용하고 있지 않은 패키지를 말한다. 이러한 패키지들은 직접 설치하지 않아도 해당 패키지를 사용할 수 있게 된다. 이런 유령 의존성의 문제는 버전 관리가 어렵기 때문에 버전 호환 에러가 발생할 수 있다.

<br>

### # package.json

- package.json의 역할

  - 프로젝트 이름, 버전, 설명 등의 정보 제공

  - 의존성 패키지 관리 (dependencies, devDependencies)

  - npm 스크립트 정의 (scripts)

  - 프로젝트에서 사용하는 모듈 버전 정의 및 관리

- dependencies, devDependencies의 차이

  개발용, 배포용 라이브러리를 구분하여 설치하기 위해 사용한다.

  | 항목         | `dependencies`                         | `devDependencies`                                  |
  | ------------ | -------------------------------------- | -------------------------------------------------- |
  | 📦 포함 여부 | 배포 시 포함됨                         | 배포 시 **제외 가능** (`npm install --production`) |
  | 🧠 용도      | 앱 **실행에 필요한** 라이브러리        | 앱 **개발/빌드/테스트에 필요한** 도구              |
  | 🛠️ 설치 명령 | `npm install <패키지명>`               | `npm install -D <패키지명>`                        |
  | 예시         | `react`, `axios`, `express`, `zustand` | `typescript`, `eslint`, `jest`, `webpack`, `vite`  |

- package-lock.json

  | 항목             | `package.json`                                                    | `package-lock.json`                                                                                                               |
  | ---------------- | ----------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
  | 🎯 목적          | 프로젝트 정보와 의존성 명세                                       | 의존성 **버전 고정** (정확한 트리 기록)                                                                                           |
  | 📦 포함 내용     | 어떤 패키지를 쓰는지, **대략적인 버전 범위** (version range 사용) | 어떤 패키지가 설치됐는지, **정확한 버전** (의존성 트리 전체, 각 패키지의 정확한 버전, 다운로드 URL, 무결성 해시 등의 정보가 포함) |
  | 🔁 업데이트 시점 | 직접 수정하거나 `npm install`로 의존성 추가 시                    | `npm install`로 패키지를 설치/제거할 때 자동 생성 또는 업데이트                                                                   |
  | 👥 협업 시 의미  | "이런 패키지들을 쓸 거야"                                         | "정확히 이 버전들이 설치돼야 해"                                                                                                  |

  설치된 의존성의 정확한 버전과 트리를 기록한 파일로 npm install 시 자동으로 생성 및 갱신되며, 협업과 배포에서 동일한 환경을 보장한다. Git 저장소에 꼭 커밋해서 팀원들이 동일한 패키지 버전을 설치하게 해야 한다.

<br>

### # FileReader와 URL.createObjectURL

이미지 미리보기와 같이 파일 입출력 관련 기능을 구현할 때 사용하는 대표적인 메소드로는 FileReader와 URL.createObjectURL 방식이 있다.

- Blob 객체와 File 객체

  - Blob 객체(바이너리 라지 오브젝트) : 이미지, 오디오, 영상 등을 다룰 때 사용하는 멀티미디어 객체이다. 사이즈나 타입 등의 정보를 담고 있다.

  - File 객체 : Blob을 상속받는 객체로 최종수정날짜(라스트모디파이드), 파일명(네임) 등의 조금 더 많은 정보를 담고 있다.

- FileReader

  - File 객체, Blob 객체 저장된 바이너리 데이터를 비동기적으로 읽어 base64 인코딩된 문자열(data URL) 또는 텍스트 등으로 변환

  - 변환된 base64 문자열을 `<img src="data:...">` 등에 바로 사용할 수 있음

- URL.createObjectURL

  - File 객체, Blob 객체를 받아서 임시로 접근 가능한 고유한 URL을 바로 생성(별도의 인코딩 과정 없이, 브라우저 메모리에 포인터만 생성하는 방식), 해당 URL은 생성된 페이지 내에서만 유효하다.

  - 페이지를 닫거나 이동할 때 반드시 URL.revokeObjectURL()을 호출해야한다. 호출하지 않으면 생성한 고유 URL은 메모리에 계속 상주하게 되어 메모리 누수가 발생할 수 있다.

- FileReader vs URL.createObjectURL

  | 항목          | FileReader                        | URL.createObjectURL                  |
  | ------------- | --------------------------------- | ------------------------------------ |
  | 결과물        | base64 인코딩된 문자열 (data URL) | 임시 고유 URL                        |
  | 메모리 사용량 | 상대적으로 높음                   | 상대적으로 낮음                      |
  | 속도          | 느림 (파일 읽고 인코딩 필요)      | 빠름 (즉시 URL 생성)                 |
  | 용량 한계     | 10MB 정도 권장                    | 800MB 이상도 가능                    |
  | 사용 후 처리  | 불필요                            | 필요, `URL.revokeObjectURL()`로 해제 |

<br>

### # import 중괄호 {}의 유무

- export 방식에서 차이가 있다. export로 내보낸 경우 이름을 그대로 활용하여 {} 중괄호로 감싸 가져와야하고 export default로 내보낸 경우 이름을 변경하여 괄호 없이 가져올 수 있다. 이 때 중괄호가 있는 경우도 as 키워드를 이용하면 이름을 바꿔 받아올 수 있다. {a as b}의 경우 a의 값을 b에 할당하여 가져온다라고 해석할 수 있다.

  ```javascript
  // App.js
  const a = 1;
  const b = 2;
  export { a };
  export const c = 3;
  export default b;
  ```

  ```javascript
  // Sub.js
  import d, { a, c as e } from "./Example";
  console.log(a, d, e); // 1, 2, 3
  ```

<br>

### # JavaScript Module, ESM(ECMAScript Modules)과 CJS(CommonJS)

- 모듈 시스템이 생겨난 이유

  모듈 시스템이 생기기 전 Javascript는 기본적으로 script 태그로 불려져 사용했었다. 하지만 하나의 javascript 파일에 작성되는 경우 가독성 및 유지보수성이 매우 떨어지고,
  javascript 파일을 분리하여 script 태그로 불려진 여러 javascript는 서로 관계가 없음에도 전역 객체 간에 의존성(전역 변수 공유)을 가지거나 스크립트 파일 로드 순서를
  수동으로 지정해야하는 등 여러 문제가 발생했다. 그래서 생겨난 것이 모듈 시스템이다. 모듈 시스템의 대표적인 포맷(문법)으로는 ESM(ECMAScript Modules)과 CJS(CommonJS)가 있다.

- ESM(ECMAScript Modules)과 CJS(CommonJS) 차이

  | 항목          | CommonJS (CJS)                                                         | ES Modules (ESM)                                              |
  | ------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------- |
  | 사용 환경     | Node.js                                                                | 브라우저 + Node.js(ESM 지원 시)                               |
  | 내보내기      | `module.exports`, `exports.foo`                                        | `export`, `export default`                                    |
  | 가져오기      | `require('...')`                                                       | `import ... from '...'`                                       |
  | 로딩 방식     | 런타임에 동기적으로, 파일 불러오는 동안 메인 스레드 차단 O             | 컴파일 타임에 정적으로, 파일 불러오는 동안 메인 스레드 차단 X |
  | 실행 시점     | 런타임에 모듈 해석                                                     | 컴파일 타임에 모듈 해석                                       |
  | 가져오기 위치 | 코드 어디서든 가능                                                     | 최상위 스코프에서만 가능 (비동기로 개선 가능)                 |
  | 트리 쉐이킹   | ❌ 불가능 (동적 require와 exports 객체 구조 때문에 정적 분석이 어려움) | ✅ 가능 (정적 구조 덕분에 정적 분석 가능)                     |
  | 파일 확장자   | `.js`, `.cjs`                                                          | `.mjs`, `.js` (with `"type": "module"`)                       |
  | 기본 방식     | Node.js에서 채택해서 사용 중                                           | 표준 모델 시스템, 최신 브라우저 및 ESM 설정된 Node.js         |

  ```javascript
  // require
  module.exports = moment;
  const moment = require("moment");
  ```

  ```javascript
  // import
  export default moment;
  import moment from "moment";
  ```

- CJS(CommonJS)가 트리쉐이킹이 안되는 자세한 이유

  1. 동적 require

  아무 위치에서나 불러올 수 있고 require() 호출과 module.exports 객체 할당이 런타임에 실행되기 때문에, 어떤 부분이 실제로 사용되는지 정적으로 파악하기 어렵다.

  ```javascript
  const lib = require(condition ? "a" : "b");
  ```

  2. exports가 객체 단위

  exports 시 객체 단위로 내보내기 때문에 번들러가 어떤 함수가 쓰이는지 알기 어려움 (구조 분해가 아님), 런타임에 동적으로 export 객체에 프로퍼티를 추가할 수 있기 때문에 정적으로 파악하기 어렵다.

  ```javascript
  // 객체 단위 export
  module.exports = {
    a: () => {},
    b: () => {},
  };

  // 런타임에 동적으로 export
  exports.add = (a, b) => a + b;

  if (someCondition) {
    exports.mul = (a, b) => a * b;
  }
  ```

<br>

### # 트리 쉐이킹 (Tree Shaking)

- 트리쉐이킹

  웹팩에서도 찾아볼 수 있고 네이밍에서도 알 수 있듯이 나무를 흔들어 필요없는 나뭇잎들을 떨어뜨린다는 뜻이다. 트리쉐이킹은 번들링 시 패키지 내부의 필요한 코드만 가져오고 필요없는 코드를
  제거하여 최적화하는 기법을 말한다. 번들 사이즈 및 빌드 시간을 줄일 수 있다. 웹팩은 ES6 이상의 import, export 표준 모듈 시스템을 사용하는 모듈에 대해 기본적인 트리쉐이킹을 지원한다.
  import 하는 패키지 내부에 사용하지 않는 export를 제거하는 것이다. 주의할 점은 ES5 이하 CommonJS 모듈 시스템을 사용하는 경우 트리쉐이킹이 적용되지 않는다. 이렇게 동작하는 이유는
  ESM은 컴파일 타임에 모듈을 로딩하기 때문에 트리쉐이킹이 가능하고 CJS는 런타임에 모듈을 로딩하기 때문에 트리쉐이킹이 불가능하다. 또한 바벨의 @babel/preset-env 사용 시 import가
  require로 변환될 수 있기 때문에 트리쉐이킹이 적용되지 않을 수 있다. 이 때 @babel/preset-env 속성 중 modules 속성을 false로 설정하면 ES 모듈을 CJS 모듈로 변환하지 않으므로
  문제를 해결할 수 있다.

- react의 컴파일 타임

  - 컴파일 타임은 코드가 브라우저에서 실행되기 전에, 번들러(예: Webpack, Vite), 트랜스파일러(예: Babel)가 코드를 해석하고 변환하는 시점이다.

  - 컴파일 타임이 빌드 타임에 포함

  - 예시 (React + TypeScript + Webpack 기준)

    - TS/JSX → JS 변환 → 컴파일 타임 (Babel, tsc)

    - JS, CSS, 이미지 등 리소스 통합/압축 → 빌드 타임 (Webpack, Vite 등)

<br>

### # **Link tag 특정 조건에서의 페이지 이동**

<br>

- Link tag 사용 시 특정 조건에서만 페이지 이동이 가능하도록 하려면 아래와 같은 코드로 작성할 수 있다.

  ```javascript
  // return문 외부
  const testHandler = (event) => {
    if (inputValue.length <= 0) event.preventDefault();
  };

  // return문 내부
  <Link className={btnClass} to="/search" key={id} onClick={testHandler}>
    <img alt="cart close icon" src={url} className={iconClass} />
  </Link>;
  ```

<br>

### # **Link tag 페이지 이동 시 props 전달하기**

<br>

- Link tag 페이지 이동 시 props를 전달할 수 있다.

  ```javascript
  <Link
    to={{
      pathname: '/search'
      state: {
        data1: year,
        data2: title,
        data3: summary
      }
    }}
  />
  ```

  전달 받은 props는 useLocation hook을 이용하여 사용할 수 있다.

  ```javascript
  import React from "react";
  import { useLocation } from "react-router";

  const Search = () => {
    const location = useLocation();
    console.log(location);
    ...
  }
  ```

<br>

### # **axios와 모듈화**

<br>

- 클라이언트에서 서버로 보내는 요청은 무수히 많기 때문에 모듈화가 거의 필수적이라고 볼 수 있다. 이미 설계된 모듈을 가져와 추가적인 HTTP method, 요청 URL, 파라미터 등만 사용하여 일관성 유지, 생산성 향상, 유지보수를 용이하게 할 수 있다. axios.create를 사용하여 axios 인스턴스를 생성하여 공통 header를 관리하고 axios interceptor request use를 통해 요청을 가로채 요청에 필요한 토큰 등을 심어줄 수 있다. 또한 axios 인스턴스를 활용하여 요청 로직을 일관되게 작성할 수 있다.

  (1) Axios 인스턴스 만들기

  ```javascript
  // api/axiosInstance.js
  import axios from "axios";

  // baseURL, headers 등 공통으로 사용할 옵션 세팅
  export const apiClient = axios.create({
    baseURL: process.env.REACT_APP_API_URL,
    headers: {
      "Access-Control-Allow-Origin": "*",
      "Content-Type": "application/json",
    },
  });
  ```

  (2) 요청을 가로채기 위한 Interceptors

  아래와 같이 인스턴스를 만든 후에는 interceptors를 활용하여 요청 시 해당 요청을 가로챈 후 추가 로직을 구현할 수 있다. 아래 코드는 토큰을 심기 위해 사용하였다.

  ```javascript
  // api/axiosInstance.js
  apiClient.interceptors.request.use((config) => {
    const accessToken = localStorage.getItem("access_token");

    if (accessToken && config.headers) {
      config.headers["Authorization"] = `Bearer ${accessToken}`;
    }
    return config;
  });
  ```

  (3) 사용 예시

  ```javascript
  // api/todos.js
  import { apiClient } from "./axiosInstance";

  export const getTodos = async () => {
    return apiClient.get("/todos");
  };

  export const createTodo = async (todo) => {
    return apiClient.post("/todos", { todo });
  };

  export const updateTodo = async (id, todo, isCompleted) => {
    return apiClient.put(`/todos/${id}`, { todo, isCompleted });
  };

  export const deleteTodo = async (id) => {
    return apiClient.delete(`/todos/${id}`);
  };
  ```

<br>

- 모듈화 장점

  (1) 일관성 유지: 인터셉터를 사용하면 여러 곳에서 헤더에 토큰을 추가하는 것을 일관성 있게 관리할 수 있다.

  (2) 재사용성: 인터셉터를 설정하면 다른 API 호출에서도 자동으로 헤더에 토큰이 추가된다.

  (3) 유지보수성 향상: 코드를 보다 간결하고 관리하기 쉽게 만든다.

<br>

### # **modal Portals로 사용하기**

<br>

(1) modal이 생성 될 위치에 div 생성 (ex public/index.html)

```html
<body>
  <noscript>You need to enable JavaScript to run this app.</noscript>
  <div id="root"></div>
  <div id="modal-root"></div>
</body>
```

(2) modal Potal 만들기

```javascript
// src/components/ModalPortal.ts
import { ReactNode } from "react";
import ReactDom from "react-dom";

interface Props {
  children: ReactNode;
}

const ModalPortal = ({ children }: Props) => {
  const el = document.getElementById("modal-root") as HTMLElement;

  return ReactDom.createPortal(children, el);
};

export default ModalPortal;
```

(3) 실제 사용할 modal 만들기

```javascript
// src/components/LoginModal/LoginModal.tsx
import styles from "./loginModal.module.scss";

const LoginModal = ({ onClose }: any) => {
  return (
    <div className={styles.loginModal}>
      <div className={styles.content}>
        <h3>아이디와 비밀번호 모두 입력해주세요.</h3>
        <button type="button" onClick={onClose}>
          닫기
        </button>
      </div>
    </div>
  );
};

export default LoginModal;
```

(4) Portal을 사용하여 modal 사용하기

```javascript
import LoginModal from "components/Modal/LoginModal/LoginModal";
import ModalPortal from "components/Modal/ModalPortal";

const Login = () => {
  ...

  return (
    <div>
      ...

      {modalOpen && (
        <ModalPortal>
          <LoginModal onClose={HandleModalShow} />
        </ModalPortal>
      )}
    </div>
  );
};

export default Login;
```

<br>

### # **useRef hook 모달 영역 밖 클릭 시 닫기**

<br>

- useRef hook을 사용하여 모달 영역 밖 클릭 시 모달이 자동으로 닫히도록 구현할 수 있다.

  ```javascript
  const userMenu = useRef();
  const [isOpen, setIsOpen] = useState(false);

  const modalCloseHandler = ({ target }) => {
    if(isOpen && !userMenu.current.contains(target)) setIsOpen(false);
  };

  useEffect(() => {
    window.addEventListener('click', modalCloseHandler);

    // 모달 특성상 컴포넌트가 unmount 되는 주기가 많으므로 useEffect 부수 효과 함수안의 리턴문을 통해 click 이벤트를 remove 한다.
    return () => {
      window.removeEventListener('click', modalCloseHandler);
    };
  });

  return (
    {
      isOpen &&
      <Modal ref={userMenu}>
        ...
      </Modal>
    }
  );
  ```

<br>

### # useRef

- React에서 특정 값을 컴포넌트 생애주기 동안 계속 저장하고 싶을 때 쓰는 훅이다. 값을 저장할 뿐만 아니라, DOM 엘리먼트에 직접 접근할 때도 주로 사용한다. current 값 변경 시 리렌더링이 발생하지 않고 다른 state로 인해 리렌더링이 발생하여도 값을 유지한다.

  ```jsx
  // 값 저장용
  import React, { useRef } from "react";

  function Timer() {
    const countRef = useRef(0);

    function handleClick() {
      countRef.current += 1; // 변경해도 리렌더링 발생 x
      console.log(countRef.current); // 값은 유지됨
    }

    return <button onClick={handleClick}>Click me</button>;
  }
  ```

  ```jsx
  // DOM 접근용
  import React, { useRef } from "react";

  function InputFocus() {
    const inputRef = useRef(null);

    function focusInput() {
      inputRef.current.focus(); // 실제 DOM input에 포커스
    }

    return (
      <>
        <input ref={inputRef} />
        <button onClick={focusInput}>Focus Input</button>
      </>
    );
  }
  ```

<br>

### # useTransition / useDeferredValue

react 18에서 useTransition, useDeferredValue 두 가지 hook이 추가되었다. 이 두 가지 hook은 기존 debouncing과 throttling이 필요한 경우 사용할 수 있다.

<br>

- useTransition

  useTransition는 state의 업데이트를 늦춰준다. 일반 setState는 긴급 업데이트로 처리되고 useTransition의 startTransition로 래핑한 setState는 일반 setState보다
  느리게 동작한다. 즉 비동기로 동작하며 배치업데이트 되던 setState의 우선 순위를 지정할 수 있다. 사용법은 useTransition가 반환하는 첫번째 객체로 state 업데이트가 진행 중임을
  감지할 수 있고 두번째 객체로 업데이트를 늦출 state를 래핑할 수 있다. 예시로 사용자 입력에 따른 값이 큰 setState의 연산이 있는 경우 입력할 때마다 딜레이가 발생할 수 있는데
  해당 setState 연산을 useTransition로 래핑하여 사용자 입력이 딜레이 되지 않도록 하고 연산 시 isPending을 통해 로딩 UI를 노출해주며 사용자 경험을 향상시킬 수 있다.

  ```javascript
  import { useState, useTransition } from "react";

  const App = () => {
    const [input, setInput] = useState("");
    const [list, setList] = useState([]);
    const [isPending, startTransition] = useTransition();
    const bigList = [...Array(10000).keys()];

    const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
      const value = e.target.value;
      setInput(value); // ✅ 긴급 업데이트: 사용자 입력 즉시 반영

      // 🕗 느린 업데이트: 무거운 작업은 나중에 천천히
      startTransition(() => {
        const filtered = bigList.filter((item) =>
          item.toString().includes(value)
        );
        setList(filtered);
      });
    };

    return (
      <div>
        <input value={input} onChange={handleChange} />
        {isPending && <div>로딩 중...</div>}
        <ul>
          {list.map((item) => (
            <li key={item}>{item}</li>
          ))}
        </ul>
      </div>
    );
  };
  ```

- useDeferredValue

  useTransition는 업데이트 순서에 직접 관여하는 반면 useDefferredValue는 업데이트 되는 값에 관여한다. useDefferredValue를 적용하는 경우 값이 완전히 처리되기 전까지
  이전 값을 표시한다. 사용법은 setState의 업데이트 값인 state를 전달받아 사용한다. 예시로 검색어 입력 중 입력 값에 따른 결과물 노출 시 검색어 입력이 완료되기 전 원하지 않는
  결과물이 노출되는 것을 막을 수 있다.

  ```javascript
  const UseDeferredValueTest = () => {
    const [query, setQuery] = useState("");
    const deferredQuery = useDeferredValue(query);

    return (
      ...
      <SearchResults query={query} />
    )
  }
  ```

<br>

### # React 18 Streaming SSR

- Streaming SSR이란

  기존 SSR의 동작 방식은 브라우저가 서버에서 렌더링이 완료된 HTML 파일(static)을 받아온 뒤 이 HTML 파일을 파싱한 후 사용자에게 우선적으로 보여준다. 그 후 javascript가 로드되면
  하이드레이션을 통해 사용자와 상호작용 가능하도록 한다. 이 때 서버에서 렌더링이 지연될 경우 TTFB가 늦어지고 이어서 FCP도 느려질 수 있다.

  또한 javascript 로드가 지연되는 경우 하이드레이션이 지연되어 TTI(사용자와 상호작용 시간)가 느려져 사용자 경험이 좋지 않아질 수도 있다. 이러한 상황을 개선하고자 React 18에서는 Streaming SSR가 추가되었다.

  `<Suspense>` 컴포넌트를 기준으로 서버에서 HTML을 청크(chunk) 단위로 나누고, 렌더링이 완료된 HTML 청크부터 스트리밍 형태로 브라우저에 전송한다. 클라이언트는 서버에서 도착하는
  HTML 청크를 순차적으로 그려나가며, 동시에 하이드레이션도 스트리밍처럼 병렬로 처리하여 전체 페이지가 준비되기 전이라도 사용자는 빠르게 일부 콘텐츠를 볼 수 있다.

  이러한 방식을 통해 TTFB, FCP, TTI를 개선하였다.

- Streaming SSR 구현 방법

  - react.js

    - `renderToPipeableStream()`(혹은 `renderToReadableStream()`) API + `<Suspense>`를 함께 사용해서 구현

  - next.js

    - Next.js에서는 Streaming SSR 기능을 App Router + 서버 컴포넌트(Server Component) 중심으로 기본적으로 자동 적용

      ```jsx
      // app/page.tsx
      import { Suspense } from "react";
      import SlowComponent from "./SlowComponent";

      export default function Page() {
        return (
          <>
            <h1>Hello</h1>
            <Suspense fallback={<p>로딩 중...</p>}>
              <SlowComponent />
            </Suspense>
          </>
        );
      }
      ```

<br>

### # React Server Component (RSC)

<br>

- React Server Component 도입 배경

  기존 React에서 Data fetching 시 대부분 아래와 같은 케이스 중 하나를 선택하여 API를 호출한다.

  - **부모 컴포넌트에서 거대한 API를 호출하여 자식의 props로 내려준다.**
  - **컴포넌트에 필요한 API를 각 컴포넌트에서 호출한다.**

  첫 번째 방법의 경우 부모 컴포넌트에서 거대한 API를 호출하여 API 요청 수를 줄일 수 있지만 데이터 오버 패칭 및 부모 컴포넌트와 자식 컴포넌트의 의존성이 높아지게 되어 재사용 및 유지보수가 어려워지게 된다.

  두 번째 방법의 경우 각 컴포넌트가 렌더링 될 때 필요한 데이터만 가져와 보여줄 수 있다는 장점이 있지만 API 요청 수가 많고 부모 컴포넌트가 렌더링 된 후 API를 요청하여 응답을 받아올 때까지 자식 컴포넌트의 렌더링과 API 호출이 지연된다. 또한 호출 지연이 발생하는 경우 나타나는 `Waterfall`로 인해 사용자 경험은 떨어지게 되고 UI가 밀리는 `Layout Shift`가 발생할 수 있다.

  또한 기존 Nextjs에서 SSR을 위해 getSeverSideProps를 사용했는데 getSeverSideProps는 중첩 컴포넌트 중 탑 레벨 컴포넌트에서만 사용이 가능했고 getSeverSideProps를 통해 받아온 데이터를 props 등으로 하위 컴포넌트로 내려주어야 한다는 문제가 있었다. 이러한 문제도 React Server Component 로 해결할 수 있다. RSC를 사용하면 서버와 클라이언트(브라우저)가 서로 협력하여 렌더링할 수 있다. 즉, 일부 컴포넌트는 브라우저에서, 일부 컴포넌트는 서버에서 렌더링할 수 있게 된다.

  마지막으로 번들 사이즈 문제도 해결할 수 있다. UI를 렌더링할 때 UI를 렌더링하는 데에는 필요하지 않은 데이터 처리 과정에 필요한 모듈까지 함께 번들링 되기 때문에 큰 프로젝트의 경우 브라우저가 받아와야 하는 파일의 용량이 매우 높아진다. 이 불필요한 청크들을 받아오는 것을 막기 위해 Code splitting이나 Lazy Loading과 같은 기술을 이용하지만 반복되는 작업과 시간 투자가 불편함으로 작용했다. 이러한 문제점도 `React Server Component`를 통해 해결할 수 있다. RSC를 사용해서 인터렉션이 없는 부분에 번들이 추가되지 않도록 할 수 있다. (Zero-Bundle)

<br>

- React Server Component의 장점

  - 자유로운 서버 리소스 접근과 빠른 데이터 패칭

    (요약 : 서버 컴포넌트는 서버에서 동작하기 때문에 데이터베이스, GraphQL, 파일 시스템, 인터널 서비스 등 서버 리소스에 직접 접근 할 수 있고 브라우저보다 더 빠르게 데이터를 가져올 수 있다.)

    서버 컴포넌트는 서버에서 동작하기 때문에 데이터베이스, GraphQL, 파일 시스템, 인터널 서비스 등 서버 사이드 데이터 소스에 직접 접근 할 수 있다. 서버는 공용 api 엔드 포인트를 거치지 않고 데이터를 직접 가져올 수 있고, 일반적으로 데이터 소스와 더 가깝게 배치되어 있으므로 브라우저보다 더 빠르게 데이터를 가져올 수 있다.서버에서 fetching한 데이터는 클라이언트 컴포넌트에 props로 전달 가능하다. 한 가지 유의해야 할 점은 json으로 인코딩 가능한 serializable props만 전달 가능하며 function은 전달할 수 없다.

  - 제로 번들 사이즈 컴포넌트

    (요약 : 서버 컴포넌트는 서버에서 렌더링 시 코드나 번들을 서버에서 다운로드하고 재사용하며 브라우저로 번들이 아닌 직렬화한 RSC 객체를 전달하여 자바스크립트 번들에 포함되지 않는다.)

    프론트엔드 앱을 개발하다 보면 무수한 라이브러리를 사용하게 된다. 직접 구현하기 까다로운 라이브러리들을 하나 둘 추가하다 보면 번들 사이즈가 늘게 되고, 퍼포먼스에 악영향을 끼치게 된다. 요즘은 많은 라이브러리들이 트리 셰이킹을 지원하고 필요에 따라 코드 스플리팅으로 렌더링에 필요한 번들 사이즈를 최대한 줄일 수 있지만 결국 번들 사이즈가 늘어나는 것은 막을 수 없다. 이것이 서버 컴포넌트가 고안 된 이유 중 하나이다. 클라이언트 컴포넌트와 다르게 서버 컴포넌트 코드는 브라우저에 다운로드 되지 않고 서버에서 미리 렌더링 된 static content를 전달하기 때문에 패키지를 추가해도 번들 사이즈에 영향을 끼치지 않는다. 즉 브라우저는 자바스크립트 번들을 모두 다운로드 해야하지만 서버는 모든 의존성을 미리 다운로드 해놓고 수시로 재사용 하기 때문에 무거운 코드 모듈을 저렴하게 사용할 수 있다. 즉 유저 인터랙션이 없는 컴포넌트들은 서버 컴포넌트로 사용하면 동일한 뷰를 제공함과 동시에 번들 사이즈와 초기 로딩 시간을 감소시킬 수 있다.

  - 자동 코드 스플리팅

    (요약 : 서버 컴포넌트에서 import 되는 모든 클라이언트 컴포넌트를 자동으로 코드 스플리팅하며 지연 로딩되는 컴포넌트를 미리 파악하여 더 빠른 번들 다운로드가 가능하다.)

    Code splitting이란 하나의 거대한 자바스크립트 번들을 여러 개의 작은 번들로 쪼개어 필요할 때마다 클라이언트로 전송하는 방법이다. 기존 클라이언트 컴포넌트에서는 `React.lazy`와 `dynamic import`를 사용하여 렌더링에 필요한 컴포넌트를 동적으로 불러왔었다. Code splitting은 앱의 퍼포먼스를 크게 향상할 수 있으나 두 가지 단점이 존재한다. 첫 번째로 lazy loading이 필요한 컴포넌트마다 일일이 `React.lazy`와 `dynamic import`를 적용해야 한다. 두 번째로는 부모 컴포넌트가 렌더링 된 이후 로딩을 시작하기 때문에 화면에 보이기 전 어느 정도의 딜레이가 존재한다는 점이다. 서버 컴포넌트는 이러한 단점을 두 가지 방식으로 해결했다. 서버 컴포넌트에서 import 되는 모든 클라이언트 컴포넌트를 Code splitting point로 간주하기 때문에 더 이상 일일이 `React.lazy`를 적용할 필요가 없어졌다. 또한 서버에서 미리 필요한 컴포넌트를 선택하기 때문에 클라이언트는 렌더링 프로세스 초기에 번들을 다운로드할 수 있다.

  - 컴포넌트 단위 SSR 전략

    기존 Nextjs에서 SSR을 위한 getSeverSideProps의 경우 중첩 컴포넌트 중 최상위 컴포넌트에서만 사용이 가능했고 받아온 데이터를 props로 내려주어야 한다는 문제가 있었다. 즉 페이지 단위 서버 사이드 렌더링 전략을 세워야했다. 하지만 서버 컴포넌트를 사용하면 컴포넌트 단위로 래핑해서 사용할 수 있기 때문에 페이지 단위가 아닌 컴포넌트 단위 서버 사이드 렌더링 전략을 세울 수 있다.

<br>

- 서버, 클라이언트, 공유 컴포넌트

  - 컴포넌트의 분류

    서버 컴포넌트가 도입되면서 리액트 컴포넌트는 크게 세 가지 컴포넌트로 분류되었다.

  - 서버 컴포넌트

    - 서버 컴포넌트란?

      - 서버에서만 렌더링되는 컴포넌트

      - 유저 인터랙티비티 제공 불가

    - 사용 시 주의사항

      - X : useState(), useReducer(), useEffect()와 같은 state / effects 사용 불가

      - X : DOM과 같은 브라우저 api 사용 불가

      - X : state / effects / 브라우저 api 사용하는 커스텀 훅 사용 불가

      - O : 데이터베이스 / 내부 서비스 / 파일시스템과 같은 server-only 데이터 사용 가능

      - O : 서버 컴포넌트 / 클라이언트 컴포넌트 / native elements (예: div, span) 임포트 및 렌더링 가능

      - O : 클라이언트 컴포넌트 props로 serializable한 데이터 전달 가능

    - 파일 네임 컨벤션

      `*.server.js` 혹은 컴포넌트 파일 내부 최상단 `use server` 선언, 모든 컴포넌트는 서버 컴포넌트가 디폴트

  - 클라이언트 컴포넌트

    - 클라이언트 컴포넌트란?

      - 클라이언트에서 렌더링 되거나 SSR을 통해 서버에서 렌더링 되는 컴포넌트

      - 유저 인터랙션 사용 가능

      - 서버 컴포넌트 도입 전 리액트 컴포넌트

    - 사용 시 주의사항

      - X : 서버 컴포넌트 import 불가, 다만 서버 컴포넌트는 클라이언트 컴포넌트에게 또 다른 서버 컴포넌트를 children props로 넘겨주는 건 가능 `예) 부모 서버 컴포넌트에서 클라이언트 컴포넌트인 ChildClient 컴포넌트와 서버 컴포넌트인 ChildServer import -> <ChildClient><ChildServer /></ChildClient>`

      - X : server-only 데이터 사용 불가

      - O : state / effects / 브라우저 api 사용 가능

    - 파일 네임 컨벤션

      `*.client.js` 컴포넌트 파일 내부 최상단 `use client` 선언, use client 에서 선언한 컴포넌트 아래 컴포넌트는 모두 클라이언트 컴포넌트로서 동작

  - 공유 컴포넌트

    - 공유 컴포넌트란?

      서버와 클라이언트에서 렌더링 되는 컴포넌트

    - 사용 시 주의사항

      - X : state / effects / 브라우저 api 사용 불가

      - X : 서버 컴포넌트 임포트 불가, server-only 데이터 사용 불가

      - O : 서버와 클라이언트 컴포넌트에서 임포트 되어 사용 가능

    - 파일 네임 컨벤션

      `*.js`

<br>

- 서버 컴포넌트(RSC)와 서버 사이드 렌더링(SSR)의 차이

  (1) 브라우저로 번들 전달 여부 : 서버 컴포넌트 번들은 클라이언트로 전달되지 않는다. 하지만 서버 사이드 렌더링의 모든 컴포넌트의 코드는 자바스크립트 번들에 포함되어 클라이언트로 전송된다.

  (2) 렌더링 전략 : 서버 컴포넌트는 페이지 레벨에 상관없이 모든 컴포넌트에서 서버에 접근 가능하여 컴포넌트 단위 SSR 전략을 세울 수 있다. 하지만 getServerSideProps의 경우 상위 레벨의 페이지에서만 사용할 수 있기 때문에 페이지 단위 SSR 전략을 세워야한다.

  (3) 데이터 리패치 시 상태 유지 : 서버 컴포넌트는 브라우저에 HTML이 아닌 RSC 객체로 전달되기 때문에 클라이언트 상태를 유지하며 데이터를 리패치 할 수 있다. 하지만 SSR의 경우 HTML로 전달되기 때문에 데이터 리패치 시 HTML 전체를 리렌더링이 하며 클라이언트 상태를 유지할 수 없다.

  (4) 결론 : 서버 컴포넌트는 서버 사이드 렌더링 대체가 아닌 보완의 수단으로 사용할 수 있다. 서버 사이드 렌더링으로 초기 HTML 페이지를 빠르게 보여주고, 서버 컴포넌트로는 브라우저로 전송되는 자바스크립트 번들 사이즈를 감소시킬 수 있다.

<br>

### # React 실행 순서 퀴즈 (with 패니지먼트 면접 시 시험지 문제)

- 첫 번째 문제 : useEffect 관련

  ```jsx
  import { useEffect, useState } from "react";

  const Main = () => {
    const [state, setState] = useState(0);

    console.log(state);

    useEffect(() => {
      setState(1); // 참고 사항 : 만약 setState(0)인 경우 콘솔에 0 -> useEffect 0까지 총 2번만 출력 됨
      console.log("useEffect", state);

      return () => {
        console.log("clean up", state);
      };
    }, [state]);

    return (
      <div className="wrap">
        <span>test1</span>
      </div>
    );
  };

  export default Main;
  ```

  ![react_실행_순서_패니지먼트_01-1](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/99ac2f3b-5038-42d3-93ab-b0aa47d44d97)

  결과는 0 -> "useEffect" 0 -> 1 -> "clean up" 0 -> "useEffect" 1 -> 1 순으로 출력된다. 즉 6번의 console log가 찍히게 된다. 왜 그런지 하나씩 살펴보자.

  1. 첫 번째 0의 경우 컴포넌트 마운트 시 컴포넌트 몸체 부분이 실행되어 출력된다.
  2. 컴포넌트 마운트 후 페인트 단계까지 완료되면 useEffect가 실행된다. 이 때 useEffect 내부에 setState가 존재하는데 setState는 비동기로 처리되기 때문에 백그라운드로 넘어가고 console.log("useEffect", state)가 먼저 실행되어 "useEffect" 0이 찍힌다.
  3. setState 처리 시 이전 값 0에서 1로 변경하기 때문에 리렌더링이 발생하게 된다.
  4. 리렌더링이 발생하여 컴포넌트 몸체 부분의 console.log(state)가 실행되고 1을 출력한다.
  5. useEffect의 dependency가 변경되었기 때문에 useEffect가 실행된다. 이 때 setState의 경우 비동기로 처리되기 때문에 백그라운드로 넘어가고 return 문 안에 클린업 함수가 존재하기 때문에 이전 useEffect 대한 클린업 함수를 실행한다. 즉 console.log("clean up", state) 실행 시 state는 이전 값을 가리키기 때문에 console.log("clean up", state)의 경우 clean up 0을 출력한다.
  6. useEffect 내부에 console.log("useEffect", state)가 실행되어 "useEffect" 1이 찍힌다.
  7. setState 처리 시 이전 값 1에서 1로 변경되기 때문에 원시 타입의 경우 불변성을 가지고 있어 새로운 메모리를 할당하는 것이 아닌 이전 값과 최신 값이 동일한 참조를 가리켜 리렌더링이 발생하지 않는 것이 맞지만 동일한 값이더라도 함수 몸체 부분은 한번 더 실행된다. 즉 비교하는 시점에서 함수 몸체 부분이 한번 더 실행되지만 실제 리렌더링은 발생하지 않는다. 그리고 그 후속 리렌더링은 건너뛰게 된다.

  - 참고 : https://legacy.reactjs.org/docs/hooks-reference.html
  - If your update function returns the exact same value as the current state, the subsequent rerender will be skipped completely.
  - If you update a State Hook to the same value as the current state, React will bail out without rendering the children or firing effects. (React uses the Object.is comparison algorithm.)

  아래 예시도 살펴보자.

  ```jsx
  import { useEffect, useState } from "react";

  const Main = () => {
    const [state, setState] = useState(0);

    console.log(state);

    return (
      <div className="wrap">
        <button onClick={() => setState(1)}>test</button>
      </div>
    );
  };

  export default Main;
  ```

  ![react_실행_순서_패니지먼트_01-2](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/3d964440-09b4-4a1b-9030-be7160a6285d)

  위 코드는 첫 번째 예시에서 같은 값으로 setState 했음에도 불구하고 함수 몸체 부분이 실행되어 마지막 콘솔이 한번 더 출력되는 과정을 테스트해보기 위한 코드이다. 위 코드에서 버튼을 10번 클릭했다고 가정해보자. 결과는 0 -> 1 -> 1 순으로 출력된다. 즉 3번의 console log가 찍히게 되고 그 이후로는 찍히지 않는다. 왜 그런지 하나씩 살펴보자.

  1. 첫 번째 컴포넌트 마운트 시 console.log(state)가 실행되고 useState의 초기 값인 0을 출력한다.
  2. 첫 번째 버튼 클릭 시 setState(1)이 동작하여 이전 값과 최신 값은 다른 참조를 가리키게 되어 리렌더링이 발생한다. 리렌더링 발생 시 함수 몸체 부분에 console.log(state)가 실행되고 업데이트 된 값이 1을 출력한다.
  3. 두 번째 버튼 클릭 시 setState(1)가 동작한다. 이 때 이전 값과 최신 값은 같은 참조를 가리키고 있어 리렌더링이 발생하지 않아야한다. 하지만 리렌더링이 발생하는 것처럼 함수 몸체 부분이 실행되어 콘솔에 1이 한번 더 출력된다. 즉 같은 값인 경우 비교하는 시점에 함수 몸체는 한번 더 실행하게 되고 그 이후 렌더링부터는 출력하지 않는 것을 알 수 있다. 용빈님이 보내주신 자료를 참고해보면 리액트에서 setState를 실행할 때 무조건 리렌더링을 수행하며 이전 값과 최신 값은 setState 호출 시에 비교하는 것이 아니라 리렌더링 후 큐에 보내졌던 setState 값을 useState hook을 통해 가져와 비교하는 것 같다. (더 자세한 내용은 아래 링크를 참고하여 더 찾아보자.. 어렵다..) 그렇기 때문에 첫번째 변경 시에는 새로운 값으로 업데이트 되었기 때문에 콘솔에 1이 한번 출력되고, 두번째 변경 시에도 같은 값이지만 우선 리렌더링이 되었기 때문에 함수 몸체 부분이 실행되어 한번 더 콘솔에 1이 출력되는 것이다. 하지만 그 이후에는 최적화를 위해 실행하지 않는다. 사실 잘 이해가 안된다.. ㅠ

  - 참고 (용빈님 답변)

    - 관련 질문 : https://github.com/facebook/react/issues/20817#issuecomment-778672150

    - 관련 코드 : https://github.com/facebook/react/blob/main/packages/react-reconciler/src/ReactFiberHooks.js#L3200-L3203

    - 스택오버플로우 : https://stackoverflow.com/questions/58208727/why-react-needs-another-render-to-bail-out-state-updates

- 두 번째 문제 : useEffect 내부 동시 setState

  ```jsx
  import { useEffect, useState } from "react";

  const Main = () => {
    const [state, setState] = useState(0);

    console.log(state);

    useEffect(() => {
      setState(1);
      console.log("useEffect", state);
      setState(2);
      console.log("useEffect", state);
      setState(3);
      console.log("useEffect", state);
    }, [state]);

    return (
      <div className="wrap">
        <span>test2</span>
      </div>
    );
  };

  export default Main;
  ```

  ![react_실행_순서_패니지먼트_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/a4dfd90a-f652-4b38-8094-8b0bb6ad3659)

  결과는 0 -> "useEffect" 0 -> "useEffect" 0 -> "useEffect" 0 -> 3 -> "useEffect" 3 -> "useEffect" 3 -> "useEffect" 3 -> 3 순으로 출력된다. 즉 9번의 console log가 찍히게 된다. 왜 그런지 하나씩 살펴보자.

  1. 컴포넌트가 마운트되면 로직단 상단에 console.log(state)가 우선 실행된다. state의 초기 값은 0이기 때문에 0을 출력한다.
  2. 브라우저 페인트 단계가 완료되면 useEffect가 실행된다. 이 때 내부 setState의 경우 비동기로 동작하기 때문에 백그라운드로 넘어가고 남은 console.log 3개가 찍히게 된다. 그렇기 때문에 "useEffect" 0이 연달아 3번 찍힌다.
  3. setState 처리 시 react는 batch update를 통해 일정 간격에 setState를 몰아서 처리하는데 가장 최종 setState 값이 3이기 때문에 3으로 변경된다. 하지만 위 예시의 경우 setState의 로직이 단순하기 때문에 3으로 처리되었지만 서로 복잡도가 다른 경우 비동기로 동작하기 때문에 결과를 보장할 수는 없다. 어쨋든 위 코드에서는 이전 값 0에서 3으로 변경되기 때문에 리렌더링이 발생하게 된다.
  4. 리렌더링이 발생하여 컴포넌트 몸체 부분의 console.log(state)가 실행되고 3을 출력한다.
  5. useEffect의 dependency가 변경되었기 때문에 useEffect가 실행된다. 이 때 setState의 경우 비동기로 처리되기 때문에 백그라운드로 넘어가고 남은 console.log 3개가 찍히게 된다. 그렇기 때문에 "useEffect" 3이 연달아 3번 찍힌다.
  6. setState 처리 시 이전 값 3에서 3으로 변경되기 때문에 원시 타입의 경우 불변성을 가지고 있어 새로운 메모리를 할당하는 것이 아닌 이전 값과 최신 값이 동일한 참조를 가리켜 리렌더링이 발생하지 않는 것이 맞지만 동일한 값이더라도 함수 몸체 부분은 한번 더 실행된다. 즉 비교하는 시점에서 함수 몸체 부분이 한번 더 실행되지만 실제 리렌더링은 발생하지 않는다. 그리고 그 후속 리렌더링은 건너뛰게 된다. (첫 번째 문제 7번과 동일한 내용)

- 세 번째 문제 : 자체적으로 만들어 봄, useEffect 동기 실행

  ```jsx
  import { useEffect, useState } from "react";

  const Main = () => {
    const [state, setState] = useState(0);

    console.log(state);

    useEffect(() => {
      const a = new Array(40000000).fill("test");
      console.log(1);
    }, []);

    useEffect(() => {
      console.log(2);
    }, []);

    return (
      <div className="wrap">
        <span>test1</span>
      </div>
    );
  };

  export default Main;
  ```

  ![react_실행_순서_패니지먼트_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/3615eb74-21c3-4661-9f48-d49dadd41e68)

  결과는 0 -> 1 -> 2 순으로 출력된다. 즉 첫 번째 useEffect는 배열을 400만개 만들어 'test' 문구를 채우는 무거운 작업을 하고 있는데도 두 번째 useEffect 보다 먼저 실행된다. 여기서 알 수 있는 점은 useEffect는 setState와 같이 비동기로 동작하여 백그라운드에 넘어가 큐에 쌓인 뒤 콜스택으로 들어오는 비동기 함수가 아니라는 점이다. 즉 페인트 이후 호출되는 특수한 함수라고 보면 된다. 위에서도 알 수 있듯이 useEffect가 여러 개인 경우 useEffect의 콜백 함수를 동기적으로 호출하고 실행하는 것을 알 수 있다. 이런 점에서 javascript의 일반 함수 흐름과 동일하게 동작하는 것을 확인할 수 있다.

  - 네 번째 문제 : 자체적으로 만들어 봄, useEffect와 자식 컴포넌트

    ```jsx
    // RenderParent.tsx
    import { useEffect, useState } from "react";
    import RenderChild1 from "./RenderChild1";
    import RenderChild2 from "./RenderChild2";
    import RenderChild3 from "./RenderChild3";
    import RenderChild4 from "./RenderChild4";

    const RenderParent = () => {
      console.log("render Parent");

      const [artistId, setArtistId] = useState("");

      useEffect(() => {
        console.log(`useEffect parent : ${artistId}`);
        setArtistId("테스트");
      }, [artistId]);

      return (
        <div>
          <RenderChild1 artistId={artistId}>
            <RenderChild2 artistId={artistId}>
              <RenderChild3 artistId={artistId} />
            </RenderChild2>
          </RenderChild1>
          <RenderChild4 artistId={artistId} />
        </div>
      );
    };

    export default RenderParent;
    ```

    ```jsx
    // RenderChild1.tsx
    import { useEffect } from "react";

    const RenderChild1 = ({ artistId, children }: any) => {
      console.log("render Child1");

      useEffect(() => {
        console.log(`useEffect 1 : ${artistId}`);
      }, [artistId]);

      return <div>{children}</div>;
    };

    export default RenderChild1;
    ```

    ```jsx
    // RenderChild2.tsx
    import { useEffect } from "react";

    const RenderChild2 = ({ artistId, children }: any) => {
      console.log("render Child2");

      useEffect(() => {
        console.log(`useEffect 2 : ${artistId}`);
      }, [artistId]);

      return <div>{children}</div>;
    };

    export default RenderChild2;
    ```

    ```jsx
    // RenderChild3.jsx
    import { useEffect } from "react";

    const RenderChild3 = ({ artistId }: any) => {
      console.log("render Child3");

      useEffect(() => {
        console.log(`useEffect 3 : ${artistId}`);
      }, [artistId]);

      return <div />;
    };

    export default RenderChild3;
    ```

    ```jsx
    // RenderChild4.tsx
    import { useEffect } from "react";

    const RenderChild4 = ({ artistId, children }: any) => {
      console.log("render Child4");

      useEffect(() => {
        console.log(`useEffect 4 : ${artistId}`);
      }, [artistId]);

      return <div>{children}</div>;
    };

    export default RenderChild4;
    ```

    ![react_실행_순서_패니지먼트_04](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/edc8d826-f909-480e-b95a-5e26c6c3cbdd)

    ```md
    render Parent
    render Child1
    render Child2
    render Child3
    render Child4
    useEffect 3 :
    useEffect 2 :
    useEffect 1 :
    useEffect 4 :
    useEffect parent :
    render Parent
    render Child1
    render Child2
    render Child3
    render Child4
    useEffect 3 : 테스트
    useEffect 2 : 테스트
    useEffect 1 : 테스트
    useEffect 4 : 테스트
    useEffect parent : 테스트
    render Parent
    ```

    위 코드는 RenderParent 컴포넌트 내부에 RenderChild1, RenderChild2, RenderChild3, RenderChild4를 자식 컴포넌트로 받아 렌더링하고 있다. 이 때 RenderChild1은 children props로 RenderChild2를 받고 있고 RenderChild2 또한 RenderChild3을 children props로 받고 있다. 이 때 콘솔 출력 결과는 위와 같다.

    1. 가장 상위 컴포넌트인 RenderParent 부터 시작해서 함수 몸체 부분의 콘솔이 찍힌다. 그리고 자식 컴포넌트들도 순차적으로 몸체 부분이 실행된다.
    2. useEffect는 가상 돔의 변화를 실제 돔에 적용시키는 Commit Phase 단계 후 브라우저 페인트 단계까지 마치고 나서 실행된다고 알고 있다. 그렇기 때문에 자식 컴포넌트를 가지고 있는 경우 자식 컴포넌트가 우선적으로 컴포넌트 렌더링 되어 리액트 엘리먼트 객체를 반환해야하므로 자식 컴포넌트의 컴포넌트 렌더링이 먼저 처리된다. 위 1번과 같은 함수 몸체 부분은 리액트 엘리먼트 객체를 반환하는 것이 아닌 몸체 부분만 실행하는 것이기 때문에 우선적으로 실행되는 것이다. 그렇기 때문에 자식 컴포넌트의 리액트 엘리먼트 객체를 반환하는 작업이 완료가 되면 자식 컴포넌트 먼저 useEffect가 돌기 때문에 useEffect는 3 -> 2 -> 1 -> 4 -> parent 순으로 실행이 된다. 이유는 useEffect는 동기적으로 실행되지만 1과 4는 같은 레벨을 가지고 있고 1의 자식으로 2와 3을 받고 있기 때문에 1의 자식 컴포넌트들의 리액트 엘리먼트 객체들이 먼저 반환되기 때문에 useEffect도 우선적으로 처리된다. depth가 가장 깊은 3이 먼저 실행되는 것을 확인할 수 있다. 그렇게 자식 컴포넌트인 3과 2가 먼저 실행된 후 렌더링 단에서 상위에 위치한 1이 실행되고 그 후 4가 실행되는 것을 볼 수 있다. 그리고 자식 컴포넌트들의 useEffect가 모두 완료된 후 최상위 부모의 useEffect가 실행된다.
    3. 최상위 부모의 useEffect가 실행되고 setState는 비동기로 동작하여 콜스택이 비어있을 때 state를 업데이트시키는데 state 업데이트가 완료되면 리렌더링이 발생한다. 그렇기 때문에 위 1 ~ 2번 과정을 반복한다. 다만 차이점은 2번에서 발생하는데 초기에 props는 비어있는 상태였다가 state가 변경되었기 때문에 props로 전달받은 state의 최신 값인 "테스트"라는 문구가 추가된 것을 볼 수 있다.
    4. 또한 추가로 최상위 부모의 useEffect는 state 변경으로 인해

<br><br><br>
