# **# useReducer hook 사용법**

## **# useReducer란?**

useReducer는 useState와 같이 state를 관리하고 업데이트할 수 있는 hook이다. useState와의 차이는 예를 들어 컴포넌트에서 관리하는 값이 딱 하나고, 그 값이 단순한 숫자, 문자열 또는 boolean 값이라면 확실히 useState 로 관리하는게 편할 수 있고 만약에 컴포넌트에서 관리하는 값이 여러개가 되어서 상태의 구조가 복잡해진다면 useReducer로 관리하는 것이 편할 수 있다.

<br>

## **# useReducer의 장점**

useReducer의 장점으로는 한 컴포넌트 내에서 State를 업데이트하는 로직 부분을 그 컴포넌트로부터 분리시키는 것을 가능하게 해준다는 것이다. 그렇게 useReducer는 State 업데이트 로직을 분리하여 컴포넌트의 외부에 작성하는 것을 가능하게 함으로써, 코드의 최적화를 이루게 해준다는 장점이 있다.

<br>

## **# useReducer 사용법**

useReducer의 사용법으로는 useReducer의 첫번째 인자로 reducer 함수, 두번째 인자는 초기값을 넣어준다. 첫번째 인자로 넘어오는 reducer 함수 내부에 switch문으로 액션을 정의하고 dispatch를 통해 reducer 함수 내부에 case를 비교하여 액션을 실행시킨다.

```js
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

export default App;
```
