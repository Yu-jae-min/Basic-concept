# [react] 이펙트 훅 (Effect Hook)

## # Effect Hook

이펙트 훅(useEffect Hook)은 컴포넌트가 렌더링 이후 수행해야 할 일을 결정한다.
여기서 렌더링 이후 수행해야 할 일은 사이드 이펙트(Side Effect)라고 하며
이펙트 훅(useEffect Hook)은 사이드 이펙트(Side Effect)를 일으키기 적절한 장소라고 볼 수 있다.

<br>

### #1 Side Effect

부작용, 부수 효과라고도 부르는 사이드 이펙트(Side Effect)는 프로그래밍에서는 부정적인 의미가 아니다. input(state & props) - output(UI) 이외의 다른 값을 조작하는 것을 의미한다. 아래의 예시에서 사이드 이펙트(Side Effect)를 확인할 수 있다.

```javascript
let count = 0;

function greetWithSideEffect(name) {
  // Input
  count = count + 1; // Side Effect!

  return `${name}님 안녕하세요!`; // Output
}
```

위 함수 안에는 input과 output이 있다. 또한 input과 output만이 아닌 함수 결과 값 이외에 함수 외부에 존재하는 값이나 상태를 변경시키는 등의 행위 ("count = count + 1")가 있는데 이것이 바로 사이드 이펙트(Side Effect)가 되는 것이다.
대표적인 사이드 이펙트(Side Effect)로는 Data Fetching, DOM에 직접 접근(ex. Event Listener 등록), 구독(ex. setInterval)과 같은 행위들이 있다.

<br>

### #2 useEffect Hook

위에서 유즈이펙트 훅(useEffect Hook)은 컴포넌트가 렌더링 된 후의 발생한다고 말하였는데
(예외: useLayoutEffect) 이 말은 useEffect가 수행되는 시점에 이미 DOM이 업데이트되었음을 보장한다는 뜻이고, 바꿔 말하면 Side Effect가 렌더링에 영향을 주지 않도록 설계되었음을 의미한다.

```javascript
function greetWithSideEffect({ name }) {
  //  input
  // Bad!
  document.title = `${name}님 안녕하세요!`; // Side Effect

  return <div>{`${name}님 안녕하세요!`}</div>; // Output
}
```

React에서는 state, props의 변화가 있을 때마다 함수가 실행되는데 이 말은 매 렌더링 때마다 함수 body에 있는 로직이 실행된다는 뜻이다. 그러므로 위와 같이 사이드 이펙트(side Effect)들을 함수의 body 자리(render)에서 실행시키면 안된다. 함수의 body 자리(render)에서 실행하게 되면 렌더링과 무관한 로직이 렌더링 과정에서 실행되기 때문에 렌더링 자체에 영향을 줘 성능 상 악영향을 끼칠 수도 있다.

> ** 리액트 리렌더링 조건 **
>
> - state 변경이 있을 때
> - 전달받은 props가 업데이트 될 때
> - 부모 컴포넌트가 렌더링 될 때
> - shouldComponentUpdate에서 true가 반환될 때
> - forceUpdate가 실행될 때

그러므로 아래와 같이 유즈이펙트 훅(useEffect Hook)을 활용하여 작성해야 한다.

```javascript
import { useEffect } from "react";

function greetWithSideEffect({ name }) {
  // Input
  // Good!
  useEffect(() => {
    document.title = `${name}님 안녕하세요!`; // Side Effect
  }, [name]);

  return <div>{`${name}님 안녕하세요!`}</div>; // Output
}
```

<br>

### #3 useEffect의 사용

useEffect는 아래와 같이 사용한다.
만약 두 번째 인자에 감지할 값을 배열로 넘겨주게 되면 해당 값들이 변경되었을 때만
실행되게 할 수도 있습니다. 두 번째 인자는 여러 개도 전달 할 수가 있다.

```javascript
  import { useEffect } from "react"

  // 사용법
  useEffect( 실행시킬 동작, [ 타이밍 ] )
  document.addEventListener("타이밍", 실행시킬 동작) // 추상화 한 예시

  // 매 렌더링마다 Side Effect가 실행되어야 하는 경우
  useEffect(() => {
    // Side Effect
  })

  // Side Effect가 첫 번째 렌더링 이후 한번 실행 되고,
  // 이후 특정 값의 업데이트를 감지했을 때마다 실행되어야 하는 경우
  useEffect(() => {
    // Side Effect
  }, [value])

  // Side Effect가 첫 번째 렌더링 이후 한번 실행 되고,
  // 이후 어떤 값의 업데이트도 감지하지 않도록 해야 하는 경우
  useEffect(() => {
    // Side Effect
  }, [])
```

<br>

### #4 useEffect를 사용한 렌더링 사이클

함수 컴포넌트의 렌더링은 기본적으로 아래 순서대로 일어난다.

![react_effect_hook_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/7d1cc1c5-b955-4e83-b74f-385dadec1f8b)

(1) 컴포넌트가 렌더링 된다. 최초로 진행되는 렌더링은 브라우저에 처음으로 이 컴포넌트가 보여졌다는 의미로 마운트(mount)라고 표현한다.
(2) useEffect 첫 번째 인자로 넘겨준 함수(callback, 즉 Side Effect)가 실행된다.
(3) state나 props가 변경된 경우 다시 렌더링(re-render)이 일어난다.
(4) useEffect는 두 번째 인자에 들어있는 의존성 배열을 체크한다.

> - 만약 두 번째 인자에 아무런 값도 넘기지 않았거나 / 인자로 넘긴 배열에 들어있는 값 중 업데이트된 것이 하나라도 있다면 첫 번째 인자로 넘겨준 함수(callback)가 실행됩니다(Side Effect).
>
> - 하나도 없거나 빈 배열이라면, 아무런 일도 하지 않습니다.

(5) 만약 앞에서 일으킨 Effect에서 state나 props를 변경시켰다면 다시 렌더링이 일어난다.
(6) 중략...
(7) 컴포넌트가 필요 없어지면 화면에서 사라진다. 컴포넌트가 브라우저의 화면에서 사라졌다는 의미로 언마운트(unmount)라고 표현한다.

<br>

### #5 Clean up Effect

side effect는 정리(clean-up)가 필요하지 않은 side effect와 정리(clean-up)가 필요한 effect가 있다. 메모리 누수가 발생하지 않도록 정리(clean-up)하는 것은 매우 중요하다.

```javascript
useEffect(() => {
  function handleScroll() {
    console.log(window.scrollY);
  }

  document.addEventListener("scroll", handleScroll);
  return () => {
    document.removeEventLisnter("scroll", handleScroll);
  };
}, []);
```

주의할 점은 다음 Effect가 일어나기 전에, 이전 Effect의 영향을 정리해줘야 한다는 것을 기억해야한다. unmount이전, update직전이다. (Render → Effect Callback → Clean Up!)
아래 코드에서 출력되는 순서를 생각해보자.

```javascript
const App = () => {
  const [count, setCount] = useState(0);

  console.log("render", count);

  useEffect(() => {
    console.log("useEffect Callback", count);
    return () => {
      console.log("cleanUp", count);
    };
  }, [count]);

  return <div onClick={() => setCount(count + 1)}>하잉</div>;
};

export default Foo;
```

> render, 0
>
> useEffect Callback, 0
>
> // 버튼 클릭
>
> render, 1
>
> cleanUp, 0
>
> useEffect Callback, 1

React가 effect를 정리(clean-up)하는 시점은 React는 컴포넌트가 마운트 해제되는 때에 정리(clean-up)를 실행한다. 하지만 effect는 한번이 아니라 렌더링이 실행되는 때마다 실행된다. React가 다음 차례의 effect를 실행하기 전에 이전의 렌더링에서 파생된 effect 또한 정리하는 이유가 바로 이 때문이다.

> ** 사용 경험 **
>
> 개인적으로 실제 사용해본 경험으로는 header를 특정 스크롤 위치에서부터 sticky 속성이 부여되는 것에 사용하였는데 반복해서 실행되는 스크롤 이벤트(side effect)에서 해당 스크롤 이벤트를 정리(clean-up)를 하였었다.

<br>

---

<br>

참고자료

1. <a href="https://ko.reactjs.org/docs/hooks-effect.html" target='_blank'>Using the Effect Hook</a>
2. <a href="https://rinae.dev/posts/a-complete-guide-to-useeffect-ko" target='_blank'>[번역] useEffect 완벽 가이드</a>
3. <a href="https://dmitripavlutin.com/react-useeffect-explanation/" target='_blank'>A Simple Explanation of React.useEffect()</a>
