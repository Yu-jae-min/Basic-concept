# **useTransition / useDeferredValue**

react 18에서 `useTransition` 과 `useDeferredValue` 두 가지 hook이 추가되었다.

이 두 가지 hook은 state 스케줄러와 관련이 있는 hook이다.

react 18 버전 공식문서를 읽어보니 즉각적인 업데이트가 필요한 state, 상대적으로 즉각적인 업데이트가 필요하지 않은 state를 나누어 관리하기 위하여 추가되었다고 한다.

예를 들어 사용자가 페이지를 전환했을 때, 그리고 사용자가 버튼을 클릭했을 때를 예시로 들어보자.

1. 첫번 째 예시인 사용자가 페이지를 전환했을 때, 이 때 사용자는 모든 데이터 로딩에 시간이 걸린다는 것을 이미 인지하고 있다.
2. 두번 째 예시인 사용자가 버튼을 클릭했을 때, 이 때 사용자는 버튼을 클릭했을 때 업데이트 되는 ui가 즉각적인 반응을 하지 않는다는 것을 예측할 수 없다.

즉 사용자 경험을 높이기 위해 이 두 가지 케이스를 나누어 볼 수 있는 것이다. 첫번째 케이스는 이미 사용자가 그럴 것이라고 예상하고 있기 때문에 상대적으로 state의 업데이트 우선 순위를 미룰 수 있다. 하지만 입력이나 즉각적인 업데이트가 필요한 두번째 케이스는 우선 순위가 높아야한다.

> 💡 react 18 에서는 fiber 라는 엔진을 개선하여 자체적인 스케줄러를 가지게 되었다. 마치 OS 처럼 작업의 우선순위를 정하고, 우선순위 높은 작업이 들어오면 먼저 처리하는 기능이 구현되었다. 무겁고 유저 경험에 중요하지 않은 작업은 우선순위를 낮춰 프레임률을 유지할 수 있다.

<br>

## **# useTransition**

`useTransition` 이라는 hook에 대해 알아보자

공식문서에는 `useTransition`에 대해 아래과 같이 설명하고 있다.

**“useTransition은 UI를 차단하지 않고 상태를 업데이트할 수 있는 React Hook입니다.”**

이게 무슨 소리지? 이해 안됨 ㅎㅎ

그냥 사용해보자

```jsx
import React, { useTransition, useState } from "react";
import "./App.css";

function App() {
  const [isPending, startTransition] = useTransition();
  const [firstCount, setFirstCount] = useState(1);
  const [secontCount, setSecondCount] = useState(10);
  const arr1 = new Array(10000).fill("1");
  const arr2 = new Array(10000).fill("2");

  const handleClick = () => {
    startTransition(() => {
      setSecondCount((prev) => prev + 10);
    });

    setFirstCount((prev) => prev + 1);
  };

  return (
    <div className="App">
      <div style={{ display: "flex" }}>
        <div style={{ width: "50%" }}>
          {arr1.map((el, index) => {
            return (
              <button key={index} onClick={handleClick}>
                {firstCount}
              </button>
            );
          })}
        </div>
        <div style={{ width: "50%" }}>
          {isPending ? (
            <div>로딩...</div>
          ) : (
            arr2.map((el, index) => {
              return (
                <button key={index} onClick={handleClick}>
                  {secontCount}
                </button>
              );
            })
          )}
        </div>
      </div>
    </div>
  );
}

export default App;
```

예시 코드는 위와 같이 작성하였다.

버튼을 클릭했을 때 count를 증가시키는 함수를 트리거 시키는데 함수 내부에서 `firstCount`, `secondCount` state를 동시에 업데이트 시켰다.

원래 같은 경우에는 state는 비동기로 동작하기 때문에 어떤 state 업데이트가 먼저 처리될 지 알 수 없었다. 즉 그냥 먼저 처리되는 state가 먼저 사용자 화면에 띄어질 것이다. 작업자가 업데이트 순서를 알 수 없다는 뜻이다.

이 때 위 코드에서 차이점은 `firstCount` 는 경우 일반적인 방법으로 state를 업데이트를 처리하였고 `secondCount`는 우선 순위를 낮춰주는 `useTransition`의 `startTransition`를 사용하여 업데이트를 처리하였다.

결과는 아래와 같다.

![useTransitionTest](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/77f34c15-8f93-4861-bb26-bfe0847df438)

버튼을 클릭함과 동시에 state 업데이트가 진행되는데 `startTransition`로 래핑하지 않은 `firstCount`가 우선적으로 처리되고 그 후 `secondCount` 가 처리되는 것을 알 수 있다.

공식 문서에 나와있는 내용으로 **일반적인 state 업데이트는 모두 기본적으로 긴급 업데이트로 처리**된다고 한다. 즉 우선 순위가 분리되지 않는다. 이 때 `useTransition`를 사용하여 우선 순위를 나누어 사용자 경험을 개선할 수 있다.

> 💡 예시 코드는 setState 함수를 사용하여 비교하였지만 setState 함수 뿐만이 아닌 함수의 우선 순위를 늦출 수 있는 것이 `useTransition` hook 이다.

<br>

### **# useDeferredValue**

`useDefferredValue` 라는 hook도 한번 써보자.

공식 문서에는 아래와 같이 설명하고 있다.

“**useDeferredValue is a React Hook that lets you defer updating a part of the UI.”**

(useDeferredValue는 UI의 일부 업데이트를 연기할 수 있는 React Hook입니다.)

위에서 사용해 본 `useTransition` 과 마찬가지로 업데이트 스케줄과 관련 된 hook이다.

이것도 사용해보자.

```jsx
import { Suspense, useState, useDeferredValue } from "react";
import SearchResults from "../data/searchResult";

const UseDeferredValueTest = () => {
  const [query, setQuery] = useState("");
  const deferredQuery = useDeferredValue(query);

  return (
    <div style={{ display: "flex", flexDirection: "column" }}>
      <div>
        <h1>deferredQuery 미적용</h1>
        <label>
          Search albums:
          <input value={query} onChange={(e) => setQuery(e.target.value)} />
        </label>
        <Suspense fallback={<h2>Loading...</h2>}>
          <SearchResults query={query} />
        </Suspense>
      </div>

      <div>
        <h1>deferredQuery 적용</h1>
        <label>
          Search albums:
          <input value={query} onChange={(e) => setQuery(e.target.value)} />
        </label>
        <Suspense fallback={<h2>Loading...</h2>}>
          <SearchResults query={deferredQuery} />
        </Suspense>
      </div>
    </div>
  );
};

export default UseDeferredValueTest;
```

예시 코드는 위와 같이 작성하였다.

위 input에는 `useDefferredValue` 를 적용시키지 않았고 아래 input은 적용시켰다.

이 때 결과 화면은 아래와 같다.

![useDeferredValue](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/f9dcc47c-16e5-4c7c-9329-234831c3dd26)

위 이미지를 보면 알 수 있듯이 `useDefferredValue` 를 적용하는 경우 값이 완전히 처리되기 전까지 이전 값을 표시하는 것을 볼 수 있다. 여기서 위에서 먼저 사용한 `useTransition` 과의 차이를 알 수 있는데 `useTransition`는 업데이트 순서에 직접 관여하는 반면 `useDefferredValue`는 업데이트 되는 값에 관여한다. 사용법도 `useTransition` 는 상태 업데이트 코드를 래핑하여 사용하는 반면 `useDefferredValue` 는 상태 업데이트 되는 값을 래핑하여 사용한다.

이 두 가지 hook을 사용해보며 `debouncing` 과 `throttling` 이 떠올랐다.

`debouncing` 과 `throttling`은 검색 기능, 무한 스크롤 등 연속적으로 트리거되는 이벤트를 최적화 시키기 위해 항상 적용시켜왔다.

아마도 새롭게 추가 된 두 가지의 hook이 `debouncing` 과 `throttling`을 대체할 수 있지 않을까 라는 생각이 들었다. 그래서 검색해보았는데 어떤 개발자 분의 좋은 글이 있어서 가져와 보았다.

- **디바운싱, 스로틀링**

  자바스크립트에서는 짧은 시간에 유저 입력 등의 이벤트가 많이 일어나는 경우 화면이 끊길 수 있다. 그래서 이런 경우 특별한 최적화가 필요하다.
  대표적인 예가 바로 자동완성이다. 구글에 검색어를 입력하면 그 아래로 추천 검색어를 쭉 띄워줘야 한다. 한 글자가 바뀔 때마다 실시간으로 업데이트하면서.

  ![debouncingAndThrottling1](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/945bae6f-d1f5-484a-ac65-e6361177490c)

  만약 유저 입력 한 번에 추천 검색어 업데이트 한 번이 일어난다면 불필요한 재랜더링이 초당 수 번씩 필요할 것이다. 그래서 정작 필요한 '진짜 검색어' 에 대한 자동완성이 느려질 수 있다. 이런 걸 방지하기 위해 디바운싱이라는 처리를 한다.
  디바운싱은 특정 함수의 호출이 너무 자주 일어나지 않도록 일정 시간 동안 함수 실행을 지연시키는 것을 말한다. 다음과 같이 훅으로 작성해볼 수 있다.

  ```jsx
  const useDebouncedEffect = (func, delay, deps) => {
    const callback = useCallback(func, deps);

    useEffect(() => {
      const timer = setTimeout(() => {
        callback();
      }, delay);

      return () => {
        clearTimeout(timer);
      };
    }, [callback, delay]);
  };
  ```

  작동은 `useEffect` 훅과 유사하지만, 함수를 실행하기 전 `delay` 시간만큼 기다리며, 그 전에 다시 업데이트될 경우 기존 함수를 실행하지 않도록 되어 있다.
  스로틀링 또한 비슷한 문제를 해결하기 위한 기법이다. 지정된 시간 동안 함수가 최대 한 번 호출되도록 제한한다. 댓글 알림 같은 걸 띄우려면 주기적으로 네트워크 요청이 필요한데, 스로틀링을 이용해서 적당한 주기를 설정할 수 있다

  **정말 모든 문제가 해결되었을까?**

  디바운싱과 스로틀링에서 적절한 딜레이를 선택하는 것은 꽤 어렵다. 딜레이가 너무 길면 유저 입력에 대한 반응도 그만큼 느려지지만, 너무 짧아도 적용하는 의미가 없어진다.
  또한 cpu 부하가 큰 작업에는 적용해도 거의 의미가 없다. 유저가 숫자를 입력하면 100,000개의 배수를 띄워 주는 페이지를 생각해 보자. 대충 생각해도 컴퓨터가 버벅일 것 같다.

  ![debouncingAndThrottling2](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/f48e0027-fdcb-48f2-9357-e76de06eceed)

  유저가 빠르게 입력할 경우, 분명히 그걸 전부 처리하는 것은 비효율적이다. 그러나 디바운싱을 적용한다면 delay 를 얼마로 주어야 할까? 그건 컴퓨터 사양에 따라 다를 것이다.
  게다가 디바운싱을 적용한다고 해도, 일단 계산을 시작하면 메인 스레드가 거기서 블록되기 때문에 다음 입력을 처리하지 못한다. 한 순간 입력을 멈추면 다음 입력을 받지 못할 정도로 프레임이 저하된다.
  사실, 디바운싱과 스로틀링은 문제를 근본적으로 해결하는 방법은 아니다. 위 시나리오에서 배수를 띄워주는 속도는 빠를수록 좋다. 다만 그걸 계산하는 동안 메인 스레드가 블록돼서 상호작용이 불가능해지는 상태가 되는 게 문제인 것이다.
  이 문제를 근본적으로 해결하려면 반응 속도는 최대한 빠르게 하되, 사용자의 상호작용이 있으면 그걸 우선적으로 처리하여 화면이 멈춘 것처럼 보이지 않게 해야 한다. 무거운 연산은 메인 스레드가 놀고 있을 때만 처리하고, 유저 입력이 들어오면 다시 거기에 집중하는 것이다.
  즉, 이벤트의 우선 순위를 나누고, 우선 순위가 높은 이벤트가 발생하면 context switch 하여 그 작업을 먼저 핸들링하면 된다. 근데 자바스크립트에는 병렬 스레드나 스케줄러가 없다.

  [출처](https://velog.io/@ktthee/React-18-%EC%97%90-%EC%B6%94%EA%B0%80%EB%90%9C-useDeferredValue-%EB%A5%BC-%EC%8D%A8-%EB%B3%B4%EC%9E%90)

위 글에서 `debouncing` 과 `throttling` 을 사용하며 생겼던 이슈들에 대해 정확히 다루고 있었다.

내가 생각했던 것과 마찬가지로 이 개발자 분도 새로운 두 가지 hook이 기존 `debouncing` 과 `throttling` 을대체할 수 있다고 생각하시는 것 같았다.

물론 생기지 얼마 되지 않은 hook을 곧바로 프로젝트에 도입하기에 어려움이 있을 수 있지만 개인 프로젝트에서 사용해보며 사용법을 익혀나가고 안정성이 보장되는 시기가 되면 그 때 적용시켜보아야겠다.

### Reference

- [React v18.0](https://react.dev/blog/2022/03/29/react-v18)
- [useTransition](https://react.dev/reference/react/useTransition)
- [useDeferredValue](https://react.dev/reference/react/useDeferredValue)
