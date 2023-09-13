# [React.js] React Server Component (RSC)

2023년 09월 12일

<br>

# 1. React Server Component 도입 배경

React에서 Data fetching 시 대부분 아래와 같은 케이스 중 하나를 선택하여 API를 호출한다.

- **부모 컴포넌트에서 거대한 API를 호출하여 자식의 props로 내려준다.**
- **컴포넌트에 필요한 API를 각 컴포넌트에서 호출한다.**

첫 번째 방법의 경우 부모 컴포넌트에서 거대한 API를 호출하여 API 요청 수를 줄일 수 있지만 데이터 오버 패칭 및 부모 컴포넌트와 자식 컴포넌트의 의존성이 높아지게 되어 재사용 및 유지보수가 어려워지게 된다.

두 번째 방법의 경우 각 컴포넌트가 렌더링 될 때 필요한 데이터만 가져와 보여줄 수 있다는 장점이 있지만 API 요청 수가 많고 부모 컴포넌트가 렌더링 된 후 API를 요청하여 응답을 받아올 때까지 자식 컴포넌트의 렌더링과 API 호출이 지연된다. 또한 호출 지연이 발생하는 경우 나타나는 `Waterfall`로 인해 사용자 경험은 떨어지게 된다.

아래 예시를 보자.

```jsx
// RscTest.tsx
import RscWrapper from "./RscWrapper";
import RscComponentA from "./RscComponentA";
import RscComponentB from "./RscComponentB";

const RscTest = () => {
  return (
    <RscWrapper>
      <RscComponentA />
      <RscComponentB />
    </RscWrapper>
  );
};

export default RscTest;
```

```jsx
// RscWrapper.tsx
import { ReactNode, useEffect, useState } from "react";

interface RscWrapperProps {
  children: ReactNode;
}

const RscWrapper = ({ children }: RscWrapperProps) => {
  const [wrapperData, setWrapperData] = useState < any > {};

  // API 요청
  useEffect(() => {
    setTimeout(() => {
      setWrapperData({
        name: "wrapperData",
      });
    }, 1000);
  }, []);

  return (
    <>
      <h1>{wrapperData.name}</h1>
      <>{wrapperData.name && children}</>
    </>
  );
};

export default RscWrapper;
```

```jsx
// RscComponentA.tsx
import { useEffect, useState } from "react";

const RscComponentA = () => {
  const [componentAData, setComponentAData] = useState < any > {};

  useEffect(() => {
    setTimeout(() => {
      setComponentAData({
        name: "componentAData",
      });
    }, 3000);
  }, []);

  return (
    <>
      <h1>{componentAData.name}</h1>
    </>
  );
};

export default RscComponentA;
```

```jsx
// RscComponentB.tsx
import { useEffect, useState } from "react";

const RscComponentB = () => {
  const [componentBData, setComponentBData] = useState < any > {};

  useEffect(() => {
    setTimeout(() => {
      setComponentBData({
        name: "componentBData",
      });
    }, 2000);
  }, []);

  return (
    <>
      <h1>{componentBData.name}</h1>
    </>
  );
};

export default RscComponentB;
```

children을 가지는 `RscWrapper` 컴포넌트의 경우 API 호출이 끝난 후 state를 업데이트 시키는데 state가 있는 경우 children이 보여지도록 하고 있다. 또한 children으로 들어간 `RscComponentA`, `RscComponentB` 컴포넌트들도 각각 필요한 API를 요청하고 있다. API를 요청하는 로직은 임의의 로직을 작성하였다.

위와 같은 상황에서 API 응답 시간은 RscWrapper 의 경우 1초, RscComponentA 의 경우 3초, RscComponentB 의 경우 2초가 걸리고 있다. 이러한 경우 RscWrapper의 렌더링, 요청, 응답, 리렌더링이 끝나기 전까지 children 컴포넌트들은 렌더링을 하지 않는다. RscWrapper의 위 동작이 완료된 후 렌더링과 API 요청을 시작하여 응답 결과를 UI로 뿌려주기까지 RscComponentA 의 경우 4초 이상, RscComponentB 의 경우 3초 이상 걸리는 것을 볼 수 있고 RscComponentA 보다 하단에 위치한 RscComponentB 의 처리가 먼저 완료되기 때문에 `Layout Shift`가 발생한다.

![Reactjs_React_Server_Component_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/c96c92b7-2606-438d-9553-66fa12ae1922)

위와 같이 부모 렌더링 → 부모 데이터 패칭 → 부모 리렌더링 → 자식 렌더링 → 자식 데이터 패칭 → 자식 리렌더링과 같이 폭포처럼 흐르는 Waterfall을 줄일 수 있는 해결책이 `React Server Component` 이다.

또 이 뿐만이 아닌 기존 SSR의 문제점을 해결할 수 있다. 기존 Nextjs에서 SSR을 위해 getSeverSideProps를 사용했는데 getSeverSideProps는 최상위 컴포넌트에서만 사용이 가능했고 getSeverSideProps를 통해 받아온 데이터를 props 등으로 하위 컴포넌트로 내려주어야 한다는 문제가 있었다. 이러한 문제도 `React Server Component` 로 해결할 수 있다. RSC를 사용하면 서버와 클라이언트(브라우저)가 서로 협력하여 렌더링할 수 있다. 즉, 일부 컴포넌트는 브라우저에서, 일부 컴포넌트는 서버에서 렌더링할 수 있게 된다.

![Reactjs_React_Server_Component_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/d4dfef89-33c5-40b1-809a-bb8043a83ab5)

마지막으로 번들 사이즈 문제도 해결할 수 있다. UI를 렌더링할 때 UI를 렌더링하는 데에는 필요하지 않은 데이터 처리 과정에 필요한 모듈까지 함께 번들링 되기 때문에 큰 프로젝트의 경우 브라우저가 받아와야 하는 파일의 용량이 매우 높아진다. 이 불필요한 청크들을 받아오는 것을 막기 위해 Code splitting이나 Lazy Loading과 같은 기술을 이용하지만 반복되는 작업과 시간 투자가 불편함으로 작용했다. 이러한 문제점도 `React Server Component`를 통해 해결할 수 있다. RSC를 사용해서 인터렉션이 없는 부분에 번들이 추가되지 않도록 할 수 있다. (Zero-Bundle)

React Server Component가 도입되면서 기존 컴포넌트들은 `RCC(React Client Component)`와 `RSC(React Server Component)` 두 종류로 분리되었다. 분리된 컴포넌트들은 확장자를 통해 분류할 수 있다. RSC의 경우 `.server.jsx`를 사용하고 RCC의 경우 `.client.jsx`를 사용한다. RCC의 경우 기존 사용하던 컴포넌트이다.

만약 둘 다 아니라면 양 쪽 모두 가능한 공유 컴포넌트이다. 이러한 분류는 개발자와 번들러 입장에서 컴포넌트를 구별하기 쉽게한다. 특히 번들러의 경우 RSC를 작동하는데 중요한 역할을 하는데 파일 이름을 검사하여 클라이언트 컴포넌트를 별도로 처리할 수 있다.

서버 컴포넌트는 서버에서, 클라이언트 컴포넌트는 클라이언트에서 실행되므로 각 컴포넌트에서 수행할 수 있는 작업에는 제한이 있다.

<br>
<br>

# 2. React Server Component 렌더링의 라이프 사이클

## 2-1. 서버가 렌더링 요청을 받는다.

서버가 렌더링 과정의 일부를 수행해야 하므로, 페이지의 라이프 사이클은 항상 서버에서 시작된다. 이 중 'root' 컴포넌트는 항상 서버 컴포넌트고, 다른 서버 또는 클라이언트를 렌더링할 수 있다. 서버는 요청에 전달된 정보에 따라 서버 컴포넌트와 어떤 props를 사용할지 결정한다. 이러한 요청은 일반적으로 특정 URL에서 페이지를 요청하는 형태로 나온다.

<br>

## 2-2. 서버가 root 컴포넌트 엘리먼트를 JSON으로 직렬화

여기에서 최종 목표는 최초 root 서버 컴포넌트를 기본 html 태그와 클라이언트 컴포넌트 placeholder 트리로 렌더링하는 것이다. 그리고 이 트리를 직렬화(json)하여 브라우저로 보내면, 브라우저가 이를 다시 역직렬화 하여 클라이언트 placeholder에 실제 클라이언트 컴포넌트를 채우고 최종 결과를 렌더링하는 작업을 수행할 수 있다.

그럼 컴포넌트를 렌더링하고 싶다면 단순히 직렬화 시 사용하는 `JSON.stringify(컴포넌트)`와 같이 사용하면 직렬화된 렌더링 트리를 얻을 수 있을까? 거의 그렇다고 볼 수는 있지만 충분하지는 않다.

react element의 구조를 다시한번 생각해보자.

```jsx
// React element for <div>oh my</div>
> React.createElement("div", { title: "oh my" })
// 객체 형태로 표현, 콘솔을 통해 확인해볼 수 있다.
{
  $$typeof: Symbol(react.element),
  type: "div",
  props: { title: "oh my" },
  ...
}

// React element for <MyComponent>oh my</MyComponent>
> function MyComponent({children}) {
    return <div>{children}</div>;
  }
> React.createElement(MyComponent, { children: "oh my" });
// 객체 형태로 표현, 콘솔을 통해 확인해볼 수 있다.
{
  $$typeof: Symbol(react.element),
  type: MyComponent  // reference to the MyComponent function
  props: { children: "oh my" },
  ...
}
```

위 코드에서 알 수 있듯이 기본 HTML 태그 엘리먼트가 아닌 컴포넌트 엘리먼트의 경우, 컴포넌트를 참조하려고 하기 때문에 직렬화 할 수 없다.

따라서 모든 것을 적절히 `JSON.stringify`를 하기 위해서는, 리액트는 [replacer function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify#the_replacer_parameter)을 `JSON.stringify`에 인자로 넘겨 준다. 관련 코드는 [여기](https://github.com/facebook/react/blob/42c30e8b122841d7fe72e28e36848a6de1363b0c/packages/react-server/src/ReactFlightServer.js#L368)에서 찾을 수 있다.

기본 HTML 태그의 경우에는 JSON으로 처리가 가능하므로 특별히 처리할 것이 없다. 만약 서버 컴포넌트라면, 서버 컴포넌트 함수를 props와 함께 호출하고, 그 결과를 JSON으로 만들어서 내려보낸다. 이렇게 하면 서버 컴포넌트가 효과적으로 렌더링된다. 여기서 목적은 모든 서버 컴포넌트를 HTML 태그로 바꾸는 것이다. 만약 클라이언트 컴포넌트라면, 사실 JSON으로 직렬화가 가능하다. 이미 필드가 컴포넌트 함수가 아닌 `모듈 참조 객체 (module reference object)`를 가리키고 있다.

<br>

### 2-2-1. Module Reference Object

RSC는 리액트 엘리먼트의 type 필드에 새로운 값을 넣을 수 있도록 `module reference` 를 제공한다. 이 값으로 컴포넌트 함수대신, 이 참조를 직렬화 한다. 그렇다면 클라이트트 컴포넌트 함수에 대한 참조를 직렬화 할 수 있는 `module reference` 객체로 변환하는 것은 어디에서 이루어지는 것일까?

이러한 작업은 번들러에서 이루어진다. 리액트 팀은 RSC를 웹팩에서 사용할 수 있는 `react-server-dom-webpack`을 [webpack loader](https://github.com/facebook/react/blob/main/packages/react-server-dom-webpack/src/ReactFlightWebpackNodeLoader.js)나 [node-register](https://github.com/facebook/react/blob/main/packages/react-server-dom-webpack/src/ReactFlightWebpackNodeRegister.js)에서 제공하고 있다. 서버 컴포넌트가 `*.client.jsx` 파일에서 가져올 때, 실제로 import 하는 것이 아닌 파일 이름과 그것을 참조하는 모듈 참조 객체(module reference object)만을 가져온다. 즉, 클라이언트 컴포넌트 함수는 서버에서 구성되는 리액트 트리의 구성요소가 아니었다.

아래 코드는 JSON 트리로 직렬화하는 예시이다.

```jsx
// ClientComponent.client.jsx
export default function ClientComponent({ children }) {
  return (
    <div>
      <h1>Hello from client land</h1>
      {children}
    </div>
  )
}

// ServerComponent.server.jsx
export default function ServerComponent() {
  return <span>Hello from server land</span>
}

// OuterServerComponent.server.jsx
import ClientComponent from './ClientComponent.client'
import ServerComponent from './ServerComponent.server'
export default function OuterServerComponent() {
  return (
    <ClientComponent>
      <ServerComponent />
    </ClientComponent>
  )
}
```

```jsx
// 직렬화 결과
{
  // ClientComponent 엘리먼트를 `module reference` 와 함께 placeholder로 배치
  $$typeof: Symbol(react.element),
  type: {
    $$typeof: Symbol(react.module.reference),
    name: "default",
    filename: "./src/ClientComponent.client.js"
  },
  props: {
    // 자식으로 Server Component가 넘어간다.
    children: {
      // Server Component는 바로 html tag로 렌더링됨
      $$typeof: Symbol(react.element),
      type: "span",
      props: {
        children: "Hello from server land"
      }
    }
  }
}
```

<br>

### 2-2-2. 직렬화 된 리액트 트리

![Reactjs_React_Server_Component_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/a4276df6-fa6f-4d90-abd8-731ad8fab962)

모든 props는 직렬화 되어야 한다. 전체 리액트 트리를 JSON 직렬화 하고 있기 때문에, 클라이언트 컴포넌트가 기본 html 태그에 전달하는 props도 직렬화 할 수 있어야 한다. 그러나 (당연하게도) 서버 컴포넌트에서는 이벤트 핸들러를 props 전달할 수 없다.

```jsx
// 서버 컴포넌트는 함수를 prop으로 넘겨줄 수 없다.
// 함수는 직렬화 할 수 없기 때문이다.
function SomeServerComponent() {
  return <button onClick={() => alert("OHHAI")}>Click me!</button>;
}
```

그러나 여기서 유의할 점은, RSC 프로세스 중에 클라이언트 컴포넌트를 마주하게 된다면, 클라이언트 컴포넌트 함수를 호출하거나 클라이언트 컴포넌트를 내림차순으로 정렬하지 않는다는 것이다. 아래 코드를 보자.

```jsx
function SomeServerComponent() {
  return <ClientComponent1>Hello world!</ClientComponent1>;
}

function ClientComponent1({children}) {
  // 클라이언트에서는 가능
  return <ClientComponent2 onChange={...}>{children}</ClientComponent2>;
}
```

위와 같이 다른 클라이언트 컴포넌트를 인스턴스화 하는 클라이언트 컴포넌트가 있는 경우 ClientComponent2 컴포넌트는 RSC 트리에서 나타나지 않는다. 대신 module reference 가 있는 엘리먼트와 ClientComponent1 컴포넌트의 props만 볼 수 있다. 그러므로 ClientComponent1 컴포넌트에 이벤트 핸들러가 있는 ClientComponent2 컴포넌트를 자식으로 보내는 것은 안전하다.

<br>

## 2-3. 브라우저가 리액트 트리를 재구조화

브라우저는 서버로 부터 JSON 결과물을 받고, 이제 브라우저에서 렌더링될 리액트 트리를 재구성하기 시작한다. type이 `module reference`인 엘리먼트를 만날 때마다, 실제 클라이언트 컴포넌트 함수에 대한 참조로 대체를 시도할 것이다.

이 작업은 다시 번들러의 도움이 필요하다. 클라이언트 컴포넌트 함수의 기능을 서버 module reference로 대체해 주었던 것도 번들러였고, 이 module reference를 브라우저가 실제 클라이언트 컴포넌 함수로 대체하는 것을 아는 것도 번들러다.

이를 그림으로 구성하면 다음과 같다.

![Reactjs_React_Server_Component_04](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/d78c7c14-15f2-416b-a3ad-20fed2e7fcf0)

이제 이 트리를 렌더링하고, DOM에 커밋한다.

<br>

### 2-3-1. Suspense에서도 같은 원리 일까?

`Suspense`에 대해서 간략하게 이야기 하자면, 아직 준비되지 않는 요소가 필요할 때 (데이터를 빠르게 가져오거나, 컴포넌트를 느리게 가져오는 등) 리액트 컴포넌트로 promise를 던질 수 있다. 이 promise는 `Suspense boundary`에서 잡을 수 있다. Suspense에서 하위 트리를 렌더링 할 때, promise가 던져질 때마다 리액트는 이 promise가 resolve 될 때 까지 리액트 하위 트리 렌더링을 일시 중지한 다음 다시 시도한다.

우리가 RSC 결과물을 만들기 위해 서버에서 서버 컴포넌트 함수를 호출 할 때, 이 함수들은 각자 필요한 데이터를 가져올 때 promise를 던질 수 있다. 그리고 [이 promise를 만나면](https://github.com/facebook/react/blob/42c30e8b122841d7fe72e28e36848a6de1363b0c/packages/react-server/src/ReactFlightServer.js#L416) 앞서와 마찬가지로 placeholder를 위치시킨다. 그리고 이 promise가 resolve되면 서버 컴포넌트 함수를 다시 호출하고, 성공하면 이 완료된 청크를 내보낸다. 실제로 `RSC 출력 스트림`을 생성하고, promise가 나타나면 일시 중지하고, 이것이 resolve되면 추가적인 청크를 스트리밍한다.

마찬가지로, 브라우저에서 fetch 함수 호출로 RSC JSON 결과물을 스트리밍하고 있다. 이 프로세스 역시 결과물에서 placeholder를 마주하거나 (서버에서 던진 promise를 맞닥뜨린 경우), 스트림에서 placeholder를 [아직 보지 못한 경우](https://github.com/facebook/react/blob/main/packages/react-client/src/ReactFlightClientStream.js) promise를 던지는 것으로 끝날 수도 있다. 또는 클라이언트 컴포넌트 module reference를 마주치지만, 아직 브라우저에 로드된 클라이언트 컴포넌트 함수를 가지고 있지 않은 경우에도 promise를 던질 수 있다.

Suspense를 활용하면 서버 컴포넌트가 데이터를 가져올 때, 서버 스트리밍 RSC 출력을 사용할 수 있으며 브라우저가 데이터를 점진적으로 렌더링하고 필요에 따라 클라이언트 컴포넌트 번들을 동적으로 가져올 수 있다.

<br>

### 2-3-2. RSC Wire format

그런데 정확히 서버가 어떤 형태의 데이터를 보내는 것일까? 정확시 어떤 데이터가 서버에서 브라우저로 스트리밍 되는 것일까?

꽤 간단한 형태로 구성되어 있다. 한줄에 JSON blob 데이터가 있고, 여기에 id로 태그되어 있는 간단한 형식이다.

```
M1:{"id":"./src/ClientComponent.client.js","chunks":["client1"],"name":""}
J0:["$","@1",null,{"children":["$","span",null,{"children":"Hello from server land"}]}]
```

`M`으로 시작하는 라인은, 클라이언트 번들에서 컴포넌트 함수를 조회하는데 필요한 정보와 클라이언트 컴포넌트 module reference를 정의 한다. `J`로 시작하는 줄은 앞서 `M`라인에서 정의된 클라이언트 컴포넌트를 참조하는 것으로, 실제 리액트 컴포넌트 element 트리를 정의한다.

이 형식의 포맷은 스트리밍으로 전송이 가능하다. 클라이언트가 전체 행을 읽는 즉시 JSON의 일부 구문을 분석하여 작업을 진행할 수 잇다. 서버가 렌더링하는 동안 Suspense boundary에 도달한 경우, resolve시 각 청크에 해당하는 여러 `J`라인을 볼 수 있다.

아래 예제를 살펴보자.

```jsx
// Tweets.server.js
import { fetch } from 'react-fetch' // React's Suspense-aware fetch()
import Tweet from './Tweet.client'

export default function Tweets() {
  const tweets = fetch(`/tweets`).json()
  return (
    <ul>
      {tweets.slice(0, 2).map((tweet) => (
        <li>
          <Tweet tweet={tweet} />
        </li>
      ))}
    </ul>
  )
}

// Tweet.client.js
export default function Tweet({ tweet }) {
  return <div onClick={() => alert(`Written by ${tweet.username}`)}>{tweet.body}</div>
}

// OuterServerComponent.server.js
export default function OuterServerComponent() {
  return (
    <ClientComponent>
      <ServerComponent />
      <Suspense fallback={'Loading tweets...'}>
        <Tweets />
      </Suspense>
    </ClientComponent>
  )
}
```

위 예제에서, RSC 스트림은 아래와 같이 나타난다.

```
M1:{"id":"./src/ClientComponent.client.js","chunks":["client1"],"name":""}
S2:"react.suspense"
J0:["$","@1",null,{"children":[["$","span",null,{"children":"Hello from server land"}],["$","$2",null,{"fallback":"Loading tweets...","children":"@3"}]]}]
M4:{"id":"./src/Tweet.client.js","chunks":["client8"],"name":""}
J3:["$","ul",null,{"children":[["$","li",null,{"children":["$","@4",null,{"tweet":{...}}}]}],["$","li",null,{"children":["$","@4",null,{"tweet":{...}}}]}]]}]
```

`J0` 은 추가 자식 컴포넌트를 갖게 되었다. `Suspense boundary`의 하위 항목으로, `@3`을 가리킨다. 여기서 흥미로운 점은 `@3`은 아직 정의 되지 않았다는 것이다. 서버가 `tweets`를 완전히 로드 하면 `Tweet.client.js` 컴포넌트에 대한 module reference를 참조하는 `M4`행과 `@3`이 있는 위치로 스왑되어야 하는 다른 리액트 트리를 정의하는 `J3`행을 출력하게 된다. 그리고 `J3`의 자식들이 `M4`에 정의된 Tweet 컴포넌트를 참조하고 있다.

한가지 또 주의 할점은, 번들러가 자동으로 `ClientComponent`와 `Tweet` 을 두 개의 개별 번들로 나누어, 브라우저가 `Tweet` 번들 다운로드를 나중으로 미룰 수 있다는 점이다.

<br>

### 2-3-3. RSC Format 사용하기

이 `RSC 스트림`을 브라우저에서 실제 리액트 엘리먼트로 어떻게 전환할까? `react-server-dom-webpack`은 [진입점 (`entrypoints`)](https://github.com/facebook/react/blob/main/packages/react-server-dom-webpack/src/ReactFlightDOMClient.js)을 가지고 있는데 여기에서 RSC 응답을 받아 리액트 엘리먼트 트리를 다시 만든다.

```jsx
import { createFromFetch } from "react-server-dom-webpack";

function ClientRootComponent() {
  // fetch() from our RSC API endpoint.  react-server-dom-webpack
  // can then take the fetch result and reconstruct the React
  // element treeconst response = createFromFetch(fetch('/rsc?...'))
  return (
    <Suspense fallback={null}>
      {response.readRoot() /* Returns a React element! */}
    </Suspense>
  );
}
```

API end point에서 RSC 응답을 읽도록 `react-server-dom-webpack`에 요청한다. 그런다음, `response.readRoot()`는 응답 스트림이 처리될 때 업데이트 되는 react element를 반환한다. 스트림을 읽기에 앞서, 아직 클라이언트가 준비되지 않았으므로 promise가 반환될것이다. 리액트는 렌더링을 재개하지만, 아직 준비되지 않은 `@3` 참조가 발견되면 또다른 promise가 던져질 것이다. 그리고 `J3`을 읽게되면 그 promise가 resolve되고, 리액트는 다시 렌더링을 재개하여 이번에는 완료할 것이다. 따라서 RSC 응답을 스트리밍할때, Suspense boundary에 의해 정의된 청크로, 현재 가지고 있는 element 트리를 계속 업데이트하고 렌더링할 것이다.

그렇다면 왜 이렇게 새로운 포맷을 만들어서 번거롭게 처리하는 것일까? 클라이언트의 목표는 리액트 element 트리를 재구성하는 것이다. HTML 을 파싱하여 react element를 만드는 것보다 이 형식을 사용하는 것이 훨씬 쉽다. 이를 통해 DOM에 최소한의 커밋으로 리액트 트리에 대한 후속 업데이트를 병합할 수 있으므로, 리액트 트리를 효과적으로 재구성할 수 있는 방향으로 검토했을 것이다.

<br>
<br>

# 3. React Server Component의 장점

리액트 공식 예제(https://github.com/reactjs/server-components-demo)를 참고하여 RSC의 장점을 알아보자.

<br>

## 3-1. 자유로운 서버 리소스 접근

서버 컴포넌트는 서버에서 동작하기 때문에 데이터베이스, GraphQL, 파일 시스템, 인터널 서비스 등 서버 사이드 데이터 소스에 직접 접근 할 수 있다. 서버는 공용 api 엔드 포인트를 거치지 않고 데이터를 직접 가져올 수 있고, 일반적으로 데이터 소스와 더 가깝게 배치되어 있으므로 브라우저보다 더 빠르게 데이터를 가져올 수 있다.

```jsx
// Note.server.js - 서버 컴포넌트
import fs from 'react-fs';
import db from 'db.server';

function Note(props) {
  // NOTE: loads *during* render, w low-latency data access on the server
  const note = db.notes.get(props.id); // 데이터베이스 접근
  const noteFromFile = JSON.parse(fs.readFile(`${id}.json`)); // 파일 접근

  if (note == null) {
    // handle missing note
  }
  return (/* render note here... */);
}
```

이렇게 서버에서 fetching한 데이터는 클라이언트 컴포넌트에 props로 전달 가능하다. 한 가지 유의해야 할 점은 json으로 인코딩 가능한 serializable props만 전달 가능하며 function은 전달할 수 없다.

<br>

## 3-2. 제로 번들 사이즈 컴포넌트

프론트엔드 앱을 개발하다 보면 무수한 라이브러리를 사용하게 된다. 직접 구현하기 까다로운 라이브러리들을 하나 둘 추가하다 보면 번들 사이즈가 늘게 되고, 퍼포먼스에 악영향을 끼치게 된다. 요즘은 많은 라이브러리들이 트리 셰이킹을 지원하고 필요에 따라 코드 스플리팅으로 렌더링에 필요한 번들 사이즈를 최대한 줄일 수 있지만 결국 번들 사이즈가 늘어나는 것은 막을 수 없다.

예를 들어 아래와 같은 클라이언트 노트 컴포넌트를 렌더링 하기 위해선 컴포넌트 코드와 `marked`, `sanitize-html` 패키지 또한 번들에 추가되어야 한다.

```jsx
// NoteWithMarkdown.client.jsx - 클라이언트 컴포넌트 = 기존의 리액트 컴포넌트

import marked from 'marked'; // 35.9K (11.2K gzipped)
import sanitizeHtml from 'sanitize-html'; // 206K (63.3K gzipped)

function NoteWithMarkdown({text}) {
  const html = sanitizeHtml(marked(text));
  return (/* render */);
}
```

하지만 이와 다르게 서버 컴포넌트 코드는 브라우저에 다운로드 되지 않고 서버에서 미리 렌더링 된 static content를 전달하기 때문에 패키지를 추가해도 번들 사이즈에 영향을 끼치지 않는다. 즉 브라우저는 자바스크립트 번들을 모두 다운로드 해야하지만 서버는 모든 의존성을 미리 다운로드 해놓고 수시로 재사용 하기 때문에 무거운 코드 모듈을 저렴하게 사용할 수 있다.

위 클라이언트 컴포넌트처럼 유저 인터랙션이 없는 컴포넌트들을 서버 컴포넌트로 마이그레이션 한다면 동일한 뷰를 제공함과 동시에 번들 사이즈와 초기 로딩 시간을 감소시킬 수 있을 것이다.

```jsx
// NoteWithMarkdown.server.jsx - 서버 컴포넌트
import marked from "marked"; // ZERO IMPACT on bundle size
import sanitizeHtml from "sanitize-html"; // ZERO IMPACT on bundle size

function NoteWithMarkdown({ text }) {
  // client component와 동일
}
```

위와 같은 장점을 가진 RSC를 활용하면 서버와 브라우저가 각자 잘 수행하는 작업을 처리할 수 있다. 서버 컴포넌트는 데이터를 가져오고 콘텐츠를 렌더링하는데 초점을 맞출 수 있으며 페이지 로딩 속도가 빨라지고 자바스크립트 번들 크기가 작아져서 사용자의 환경이 향상될 수 있다.

<br>

## 3-3. 자동 코드 스플리팅

리액트 앱 퍼포먼스에 관심이 있는 개발자라면 [Code splitting](https://ko.reactjs.org/docs/code-splitting.html) 컨셉에 친근할 것이다. Code splitting이란 하나의 거대한 자바스크립트 번들을 여러 개의 작은 번들로 쪼개어 필요할 때마다 클라이언트로 전송하는 방법이다.

기존 클라이언트 컴포넌트에서는 `React.lazy`와 `dynamic import`를 사용하여 렌더링에 필요한 컴포넌트를 동적으로 불러왔었다.

```jsx
// PhotoRenderer.js
// NOTE: *before* Server Components
import React from "react";

// one of these will start loading *when rendered on the client*:
const OldPhotoRenderer = React.lazy(() => import("./OldPhotoRenderer.js"));
const NewPhotoRenderer = React.lazy(() => import("./NewPhotoRenderer.js"));

function Photo(props) {
  // Switch on feature flags, logged in/out, type of content, etc:
  if (FeatureFlags.useNewPhotoRenderer) {
    return <NewPhotoRenderer {...props} />;
  } else {
    return <OldPhotoRenderer {...props} />;
  }
}
```

Code splitting은 앱의 퍼포먼스를 크게 향상할 수 있으나 두 가지 단점이 존재한다. 첫 번째로 lazy loading이 필요한 컴포넌트마다 일일이 `React.lazy`와 `dynamic import`를 적용해야 한다. 두 번째로는 부모 컴포넌트가 렌더링 된 이후 로딩을 시작하기 때문에 화면에 보이기 전 어느 정도의 딜레이가 존재한다는 점이다.

서버 컴포넌트는 이러한 단점을 두 가지 방식으로 해결했다. 서버 컴포넌트에서 import 되는 모든 클라이언트 컴포넌트를 Code splitting point로 간주하기 때문에 더 이상 일일이 `React.lazy`를 적용할 필요가 없어졌다. 또한 서버에서 미리 필요한 컴포넌트를 선택하기 때문에 클라이언트는 렌더링 프로세스 초기에 번들을 다운로드할 수 있다.

```jsx
// PhotoRenderer.server.js - Server Component
import React from "react";

// one of these will start loading *once rendered and streamed to the client*:
import NewPhotoRenderer from "./NewPhotoRenderer.client.js";
import OldPhotoRenderer from "./OldPhotoRenderer.client.js";

function Photo(props) {
  // Switch on feature flags, logged in/out, type of content, etc:
  if (FeatureFlags.useNewPhotoRenderer) {
    return <NewPhotoRenderer {...props} />;
  } else {
    return <OldPhotoRenderer {...props} />;
  }
}
```

<br>
<br>

# 4. 서버, 클라이언트, 공유 컴포넌트

서버 컴포넌트가 도입되면서 리액트 컴포넌트는 크게 세 가지 컴포넌트로 분류되었다. React 18 이전에 사용되던 리액트 컴포넌트는 클라이언트 컴포넌트로 분류되고, 서버와 공유 컴포넌트가 추가되었다. 컴포넌트의 타입은 파일 네임 컨벤션으로 구분되며 각 타입에 맞게 컴포넌트 네임을 변경해야 한다. 기존 리액트 컴포넌트는 사용되는 방식에 따라 서버나 공유 컴포넌트로 변경될 수 있다.

| 타입                      | 설명                                                                                                                                            | 주의사항                                                                                                                                                                                                                                                                                                                                                                                                                                                    | 파일 네임 컨벤션 |
| :------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------------- |
| 서버 컴포넌트 (RSC)       | • 서버에서만 렌더링되는 컴포넌트<br>• 유저 인터랙티비티 제공 불가                                                                               | • X : useState(), useReducer(), useEffect()와 같은 state / effects 사용 불가<br>• X : DOM과 같은 브라우저 api 사용 불가<br>• X : state / effects / 브라우저 api 사용하는 커스텀 훅 사용 불가<br>• O : 데이터베이스 / 내부 서비스 / 파일시스템과 같은 server-only 데이터 사용 가능<br>• O : 서버 컴포넌트 / 클라이언트 컴포넌트 / native elements (예: div, span) 임포트 및 렌더링 가능<br>• O : 클라이언트 컴포넌트 props로 serializable한 데이터 전달 가능 | `*.server.js`    |
| 클라이언트 컴포넌트 (RCC) | • 클라이언트에서 렌더링 되거나 SSR을 통해 서버에서 렌더링 되는 컴포넌트<br>• 유저 인터랙션 사용 가능<br>• 서버 컴포넌트 도입 전 리액트 컴포넌트 | • X : 서버 컴포넌트 import 불가, 다만 서버 컴포넌트는 클라이언트 컴포넌트에게 또 다른 서버 컴포넌트를 children props로 넘겨주는 건 가능 `예) <ClientTabBar><ServerTabContent /></ClientTabBar>`<br>• X : server-only 데이터 사용 불가<br>• O : state / effects / 브라우저 api 사용 가능                                                                                                                                                                     | `*.client.js`    |
| 공유 컴포넌트             | • 서버와 클라이언트에서 렌더링 되는 컴포넌트                                                                                                    | • X : state / effects / 브라우저 api 사용 불가<br>• X : 서버 컴포넌트 임포트 불가, server-only 데이터 사용 불가<br>• O : 서버와 클라이언트 컴포넌트에서 임포트 되어 사용 가능                                                                                                                                                                                                                                                                               | `*.js`           |

<!--
| 타입                          | 설명                                                                         | 주의사항 | 파일 네임 컨벤션 |
| ----------------------------- | ---------------------------------------------------------------------------- | -------- | ---------------- |
| 서버 컴포넌트 (RSC)           | • 서버에서만 렌더링되는 컴포넌트                                             |
| • 유저 인터랙티비티 제공 불가 | • X : useState(), useReducer(), useEffect()와 같은 state / effects 사용 불가 |

• X : DOM과 같은 브라우저 api 사용 불가
• X : state / effects / 브라우저 api 사용하는 커스텀 훅 사용 불가
• O : 데이터베이스 / 내부 서비스 / 파일시스템과 같은 server-only 데이터 사용 가능
• O : 서버 컴포넌트 / 클라이언트 컴포넌트 / native elements (예: div, span) 임포트 및 렌더링 가능
• O : 클라이언트 컴포넌트 props로 serializable한 데이터 전달 가능 | Example.server.js |
| 클라이언트 컴포넌트 (RCC) | • 클라이언트에서 렌더링 되거나 SSR을 통해 서버에서 렌더링 되는 컴포넌트
• 유저 인터랙션 사용 가능
• 서버 컴포넌트 도입 전 리액트 컴포넌트 | • X : 서버 컴포넌트 import 불가, 다만 서버 컴포넌트는 클라이언트 컴포넌트에게 또 다른 서버 컴포넌트를 children props로 넘겨주는 건 가능 `예) <ClientTabBar><ServerTabContent /></ClientTabBar>`
• X : server-only 데이터 사용 불가
• O : state / effects / 브라우저 api 사용 가능 | Example.client.js |
| 공유 컴포넌트 | • 서버와 클라이언트에서 렌더링 되는 컴포넌트 | • X : state / effects / 브라우저 api 사용 불가
• X : 서버 컴포넌트 임포트 불가, server-only 데이터 사용 불가
• O : 서버와 클라이언트 컴포넌트에서 임포트 되어 사용 가능 | Example.js | -->

서버와 클라이언트 컴포넌트는 많은 차이가 있지만 차이점을 간단하게 이야기하자면 아래와 같다.

- 클라이언트 컴포넌트는 파일 시스템 접근과 같은 server-only feature를 사용할 수 없다.
- 서버 컴포넌트는 state와 같은 client-only feature를 사용할 수 없다.
- 클라이언트 컴포넌트는 다른 클라이언트 컴포넌트만 import할 수 있다. 서버 컴포넌트는 import 할 수 없지만 서버 컴포넌트 내부에서 클라이언트 컴포넌트를 import 하여 다른 서버 컴포넌트를 children props로 넘겨줄 수 있다.

  ```jsx
  // ClientComponent.client.jsx
  // 안됨.
  import ServerComponent from "./ServerComponent.server";
  export default function ClientComponent() {
    return (
      <div>
        <ServerComponent />
      </div>
    );
  }
  ```

  ```jsx
  // ClientComponent.client.jsx
  export default function ClientComponent({ children }) {
    return (
      <div>
        <h1>Hello from client land</h1>
        {children}
      </div>
    )
  }

  // ServerComponent.server.jsx
  export default function ServerComponent() {
    return <span>Hello from server land</span>
  }

  // OuterServerComponent.server.jsx
  // OuterServerComponent 는 클라와 서버 모두에서 초기화 가능하다
  // 따라서 서버 컴포넌트를 클라이언트 컴포넌트의 children으로 보낼 수 있다.
  import ClientComponent from './ClientComponent.client'
  import ServerComponent from './ServerComponent.server'
  export default function OuterServerComponent() {
    return (
      <ClientComponent>
        <ServerComponent />
      </ClientComponent>
    )
  }
  ```

리액트 서버 컴포넌트의 도입으로 기존 컴포넌트는 목적에 따라 서버(data fetching), 클라이언트(유저 인터랙션) 그리고 공유 컴포넌트로 세분화할 수 있다. 그리고 관심사에 따라 컴포넌트 타입을 지정함으로서 서버와 클라이언트 로직을 분리할 수 있게 되었다.

<br>
<br>

# 5. 미래의 리액트 컴포넌트

위에 설명한 서버 컴포넌트의 특징과 장점들을 적극 활용한다면 미래의 리액트 컴포넌트는 아래의 예시와 같이 작성할 수 있다.

```jsx
// Note.server.jsx
import { format } from "date-fns"; // 번들사이즈에 영향 없음
import { readFile } from "react-fs"; // 번들사이즈에 영향 없음
import path from "path";

import NotePreview from "./NotePreview"; // 공유 컴포넌트
import EditButton from "./EditButton.client"; // 클라이언트 컴포넌트, 자동 코드 분할됨

export default function Note({ selectedId }) {
  const note = readFile(path.resolve(`./notes/${selectedId}.md`), "utf8"); // 파일 시스템에서 data fetching

  if (note === null) {
    return (
      <div className="note--empty-state">
        <span className="note-text--empty-state">노트를 찾을 수 없어요 🥺</span>
      </div>
    );
  }

  // 노트가 존재하지 않을 시 아래의 코드는 클라이언트에 전달되지 않음
  let { id, title, body, updated_at } = note; // serializable한 props 클라이언트 컴포넌트로 전달 가능
  const updatedAt = new Date(updated_at);

  return (
    <div className="note">
      <div className="note-header">
        <h1 className="note-title">{title}</h1>
        <div className="note-menu" role="menubar">
          <small className="note-updated-at" role="status">
            마지막 변경 시간 {format(updatedAt, "yyyy MMM d 'at' h:mm bb")}
          </small>
          <EditButton noteId={id}>수정</EditButton>
        </div>
      </div>
      <NotePreview body={body} />
    </div>
  );
}
```

서버 컴포넌트가 도입됨으로써 백엔드 데이터 직접 접근, 번들 사이즈 감소, 자동 Code Splitting이 가능하게 되었고, 이로 인해 미래의 리액트 애플리케이션은 각 컴포넌트의 역할에 집중하여 개발할 수 있으며 애플리케이션의 퍼포먼스 또한 향상될 수 있을 것이다.

<br>
<br>

# 6. RSC와 SSR

최근 들어 클라이언트 사이드 렌더링의 한계점이 논쟁이 되며 [Next.js](https://nextjs.org/)나 [Remix](https://remix.run/)와 같은 서버 사이드 렌더링 프레임워크가 인기를 얻고 있다. 덕분에 서버 컴포넌트 또한 많은 관심을 받았지만 ‘서버’가 들어간 이름과 서버에서 렌더링 된다는 점 때문에 서버 사이드 렌더링과 혼동되고 서로를 대체할 수 있는 기술로 오해되고는 한다. 하지만 리액트 서버 컴포넌트는 서버 사이드 렌더링의 대체재가 아니다. 하지만 사용자 경험 향상을 위해 함께 사용할 수는 있다.

<br>

## 6-1. **서버 사이드 렌더링(SSR)이란?**

기본적인 리액트 애플리케이션은 아래와 같은 클라이언트 사이드 렌더링(CSR)으로 동작한다. (Next.js의 경우 SSG 혹은 SSR)

![Reactjs_React_Server_Component_05](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/7a447336-c9db-4949-8bea-aca2abd75438)

클라이언트 사이드 렌더링을 사용하는 앱의 경우 페이지 진입 시 HTML, 자바스크립트 그리고 모든 데이터가 로드되고 컴포넌트 렌더링이 끝나기 전까지 사용자는 아무런 기능이 없는 빈 화면만 보게 된다. 자바스크립트 번들의 용량이 크거나 사용자의 네트워크 속도가 느릴수록 초기 로딩 속도가 길어져 사용자는 오랜 시간 빈 화면을 보게 되고 이는 사용자 경험을 저하시킨다.

반면 Next.js와 같은 서버 사이드 렌더링(SSR) 구현이 가능한 프레임워크에서 서버 사이드 렌더링 사용 시 페이지 진입 시 서버에서 먼저 HTML을 렌더링하여 브라우저로 전송하고 자바스크립트 번들을 로드한다. 브라우저는 전송받은 HTML을 우선 사용자에게 보여주어 자바스크립트 번들이 다운로드 되는 동안 의미 있는 콘텐츠를 사용자에게 제공하고 자바스크립트 번들이 모두 다운로드 완료되면 [hydration](https://github.com/reactwg/react-18/discussions/46#discussioncomment-846714)을 통해 컨텐츠가 사용자와 상호 작용할 수 있도록 한다.

서버 사이드 렌더링의 가장 큰 목적은 non-interactive한 버전의 클라이언트 컴포넌트를 최대한 빠르게 브라우저에 전달하여 초기 페이지의 `First Contentful Paint` 또는 `Largest Contentful Paint` 속도를 향상시는 것이다.

우리가 흔히 이용하는 넷플릭스의 메인 페이지를 생각해보자. 무거운 프리뷰 비디오가 다운로드 되기 까지 시간이 오래 걸리지만 빈 화면 대신 이미 콘텐츠 제목, 설명, 메인 이미지가 채워진 페이지를 제공하기 때문에 기다리는 동안 사용자의 시선을 끌 수 있고 이는 사용자 경험과 만족도에 큰 영향을 미칠 것이다.

<br>

## 6-2. 서버 컴포넌트(RSC)와 서버 사이드 렌더링(SSR)의 차이

서버 컴포넌트와 서버 사이드 렌더링은 서버에서 렌더링 된다는 유사점이 있지만 해결하고자 하는 문제점이 다르다. 서버 사이드 렌더링은 응답 받은 트리를 raw html로 렌더링하기 위한 환경을 시뮬레이션 한다. 즉, 서버와 클라이언트 컴포넌트를 별도로 구별하지 않고 동일한 방식으로 렌더링한다. 서버 사이드 렌더링 프레임워크인 Next.js를 예시로 미리 언급한 서버 컴포넌트의 특징과 비교해보면 아래와 같은 [차이점](https://news.ycombinator.com/item?id=25499171)을 가지고 있다.

- 서버 컴포넌트의 코드는 클라이언트로 전달되지 않는다. 하지만 서버 사이드 렌더링의 모든 컴포넌트의 코드는 자바스크립트 번들에 포함되어 클라이언트로 전송된다.
- 서버 컴포넌트는 페이지 레벨에 상관없이 모든 컴포넌트에서 서버에 접근 가능하다. 하지만 Next.js의 경우 가장 top level의 페이지에서만 `getServerProps()`나 `getInitialProps()`로 서버에 접근 가능하다.
- 서버 컴포넌트는 클라이언트 상태를 유지하며 refetch 될 수 있다. 서버 컴포넌트는 HTML이 아닌 특별한 형태로 컴포넌트를 전달하기 때문에 필요한 경우 포커스, 인풋 입력값 같은 클라이언트 상태를 유지하며 여러 번 데이터를 가져오고 리렌더링하여 전달할 수 있다. 하지만 SSR의 경우 HTML로 전달되기 때문에 새로운 refetch가 필요한 경우 HTML 전체를 리렌더링 해야 하며 이로 인해 클라이언트 상태를 유지할 수 없다.

![Reactjs_React_Server_Component_06](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/783c0e36-8a96-4aaa-a072-464e9afb51de)

서버 컴포넌트는 서버 사이드 렌더링 대체가 아닌 보완의 수단으로 사용할 수 있다. 서버 사이드 렌더링으로 초기 HTML 페이지를 빠르게 보여주고, 서버 컴포넌트로는 클라이언트로 전송되는 자바스크립트 번들 사이즈를 감소시킨다면 사용자에게 기존보다 훨씬 빠르게 인터랙팅한 페이지를 제공할 수 있을 것이다.

<br>
<br>

# 7. RSC Q&A

## 7-1. RSC를 통한 데이터 패칭은 단순히 클라이언트 컴포넌트에서의 데이터 패칭보다 나을까?

어차피 콘텐츠를 가져오기 위해 서버에 API 요청을 해야 한다면, 이것이 현재 자주 사용하고 있는 방식, 즉 데이터를 가져오고 클라이언트에서 렌더링하는 것보다 더 나은 방법인 걸까?

결론부터 이야기 하자면 화면에 렌더링하는 내용에 따라 다르다. RSC를 사용하면 비정규화(denormalized)된, 즉 이미 '처리된' 데이터를 사용자에게 직접 매핑할 수 있으므로, 가져오는 데이터의 작은 부분만 렌더링하거나 렌더링 자체가 브라우저로 다운로드 되는 것을 피하고 싶은 자바스크립트를 필요로 할 때 (렌더링 하는데 많은 자바스크립트 코드(번들)가 다운로드 되어야 하는 경우) 도움이 될 수 있다. 또한 렌더링시 서로 의존성이 얽혀 있는 여러 데이터를 가져와야 하는 경우, 브라우저 보다는 지연시간이 짧은 서버에서 처리해서 가져오는 것이 훨씬 나을수 있다.

<br>

## 7-2. RSC에서 프레임워크를 사용해야 하는 이유는 무엇일까?

리액트 팀은 RSC가 처음에는 플레인 리액트 프로젝트 대신에 nextjs, shopify hydrogen과 같은 프레임워크를 사용해야 한다고 언급했다. 왜그랬을까?

그 이유는 개발자들의 편의성 때문이다. 프레임워크는 보다 쉽게 래퍼와 추상화를 제공하므로, 앞서 언급했던 것처럼 서버에서 RSC 스트림을 생성하거나, 브라우저에서 이를 사용할 준비같은 것을 할 필요가 없다. 이 프레임워크들은 또 SSR을 제공하며, 서버 컴포넌트를 사용할 경우 서버에서 생성된 html에 hydrate도 제공해준다.

앞서 언급했던 것처럼, 브라우저 클라이언트 컴포넌트에 적절하게 데이터를 내려주고 사용하기 위해서는 번들러의 도움이 필수적이다. 이미 webpack에 내장되어 있으며, shopify에서는 [vite로 사용할 수 있는 준비](https://github.com/facebook/react/pull/22952)를 하고 있는 것 같다. RSC에 필요한 많은 부분이 npm에 공개 패키지로 올라와 있지 않기 때문에, 이러한 플러그인 들은 리액트 저장소의 일부가 되어야 한다. 그러나 일단 개발되면, 프레임워크 없이도 사용가능해야 할 것이다.

<br>
<br>

# 8. 개발자 단톡방 대화 (w 용빈님)

개발자 단톡방에서 임용빈님이 RSC에 대해 말씀하신 내용들을 가져와 보았다.

- use client 때려박아도 기본 동작이 SSG내지 SSR이라서 서버 자원을 더 편하게 쓸 수 있다.
- 가장 많이 오해하는 게 클라이언트 컴포넌트(RCC)의 기본 동작은 CSR이 아니다. 정적 추출 가능한 데이터라면 SSG 아니라면 SSR이 기본 동작이다.
- RSC가 나왔다고 백엔드를 안 만들어도 되는 건 아니다. 하지만 서버 액션은 쓸만하다.
- 사실 넥스트 서버 단계에서 db찌르던 리액트 팀 예제가 많은 혼선을 빚은건데 그렇게 쓰면 안되고 백엔드랑 같이 쓰는 게 데이터 관리 측면에서 훨씬 좋다.
- 그냥 말 그대로 백엔드 API를 호출하는 거다. BFF로 볼 이유도 없다.
- 서버 액션과 RSC가 remote API를 대체하는 수단이 절대 아니다.
- 나는 서버 액션의 가장 큰 이점은 next server cache(fetch할 때 그 캐시)를 클라이언트 단계에서 컨트롤이 가능하다는 점으로 본다. 클라이언트에서 서버 액션을 호출할 수 있는 거 아니었으면 서버액션 쳐다보지도 않았을 것이다.
- 서버액션으로 하면 캐시가 되는 방식은 on-demand 방식으로 사용할 수도 있다. (https://nextjs.org/docs/app/building-your-application/data-fetching/fetching-caching-and-revalidating#on-demand-revalidation)
- 서버로부터 open API spec을 받은 다음에 typescript-fetch로 api client 추출하고 그러니까 뭐랄까 기존 getServersideProps에서 SSR 위해서 RSC, RCC에서 호출해서 쓰고 있다. 그리고 워터폴 문제 해결을 위해서라도 내가 어떤 정보가 필요한지 최대한 이 정보를 상단에 알려줄 필요가 있어서 Remote API가 없으면 워터폴 최적화가 매우 어려워진다. 그래서 서버액션은 최대한 보조해주는 방향으로만 사용한다. 근데 서버액션 자체가 실험단계라서 어떻게 변경될지는 잘 모르겠다.
- 다른 개발자님의 질문
  - Q : 근데 지금 RSC에서 가장 아쉬운부분이 서버 컴포넌트랑 클라이언트 컴포넌트에서 같은 상태를 공유하려면 너무 귀찮은거 같다.
  - A(용빈님) : 그거 서버에서 받은다음에 클라이언트로 props로 내리는 게 최선이다.
  - Q : 댓글 무한스크롤을 만들려하는데 첫페이지는 RSC로 보여주고 다음 페이지부터는 무한스크롤 하려하면 이거 구현할 때 보일러플레이트가 너무 많다.
  - A(용빈님) : 그거 그냥 RCC로 구현하고 SSR 처리하는게 가장 깔끔하다. 그렇게 인터렉션 많은 컴포넌트는 RSC가 비효율적이에요. RSC가 인터렉션 없는 부분인데도 번들로 추가되는 게 싫어서 나온건데 인터렉션 있는 부분이라면 그냥 기존처럼 SSR 처리하는 게 맞다. 아니면 최외곽에 RSC로 래핑하는 컴포넌트 만들어서 RCC 컴포넌트에서 초깃값 받아서 처리하고 그 이후부터 API 페이지 1씩 더해서 받는 식으로 해야하는데 이거 중복코드가 RSC, RCC 양쪽에 작성된다.

<br>
<br>

# # 참고 URL

- https://nextjs.org/docs/app/building-your-application/rendering/server-components
- https://nextjs.org/docs/app/building-your-application/rendering/client-components
- https://nextjs.org/docs/app/building-your-application/rendering
- https://react.dev/blog/2020/12/21/data-fetching-with-react-server-components
- https://github.com/reactjs/server-components-demo/tree/main
- https://programming119.tistory.com/252
- https://nextjs.org/docs/app/building-your-application/data-fetching/fetching-caching-and-revalidating#on-demand-revalidation
- https://yceffort.kr/2022/01/how-react-server-components-work
- https://tech.kakaopay.com/post/react-server-components/

<br>
