# [React.js] useMemo와 useCallback

2023년 09월 07일

<br>

# 1. useMemo와 UseCallback

useMemo와 useCallback은 작업하며 종종 사용하는 hook이다. useMemo의 경우 값을 메모이징하여 사용하고 useCallback의 경우 함수를 메모이징하여 사용한다. 즉 의존성 배열의 변화가 없는 경우 초기 렌더링 이후 동일한 계산의 반복을 제거하여 메모이징 된 값을 재사용한다는 것이다.

나의 경우 useCallback보다 useMemo를 종종 사용하는데 값을 메모이징하거나 return 문 내부에 map 메소드 등을 렌더단에서 로직단으로 분리해주기 위해 사용하고는 한다.

또한 두 hook을 사용할 때 메모리 낭비를 방지하기 위해 조건을 세워 사용하는데 의존성 배열의 변화가 잦을 경우 사용하지 않는다. 왜냐하면 의존성 배열의 변화가 잦은 경우 계속해서 변한다는 것인데 계속 변하는 값을 굳이 메모이징하여 사용할 필요가 없기 때문이다.

자주 사용하는 두 hook에 대해 사용하는 이유와 효과에 대해 다시 한번 복기해보려고 한다.

<br>
<br>

# 2. useMemo 예시

간단한 useMemo 예시를 살펴보자.

```jsx
import { useState } from "react";

const getTextHandler = () => {
  console.log("getTextHandler trigger");

  return "Hello.";
};

const UseMemoTest = () => {
  const [isOpen, setIsOpen] = useState(false);
  const text = getTextHandler();

  return (
    <div>
      <button onClick={() => setIsOpen((prev) => !prev)} />
      <h1>{text}</h1>
    </div>
  );
};

export default UseMemoTest;
```

해당 코드를 살펴보면 getTextHandler 함수가 반환하는 text를 뿌려주고 있고 버튼을 클릭했을 때 boolean 타입의 state가 업데이트 된다.

우선 초기 렌더링에 getTextHandler 함수 내부 콘솔 메세지가 나타나는 것을 볼 수 있고 버튼을 클릭하여 state가 업데이트 될 때마다 콘솔 메세지가 계속해서 찍히는 것을 볼 수 있다. 즉 리렌더링 될 때마다 getTextHandler 함수 내부 연산이 계속해서 수행되는 것이다.

위 동작을 보면 알 수 있듯이 컴포넌트는 렌더링 시 내부 객체들을 모두 초기화한다. 이 때 useMemo를 사용하여 값을 메모이징 할 수 있다.

```jsx
const text = useMemo(() => getTextHandler(), []);
```

위와 같이 정적인 text를 반환하는 getTextHandler 호출문을 useMemo로 래핑하면 초기 렌더링에만 콘솔 메세지가 찍히고 리렌더링 시 콘솔 메세지가 찍히지 않는 것을 볼 수 있다.

또 다른 예시를 보자.
아래 코드는 부모 컴포넌트인 Parent에서 자식 컴포넌트인 Child에 props를 넘기고 그 props를 활용하여 UI를 그려주는 코드이다.

```jsx
import Child from "./Child";

const Parent = () => {
  return (
    <div>
      <Child number={123} text={"hello"} />
    </div>
  );
};

export default Parent;
```

```jsx
import { useState } from "react";

const getNumber = (number) => {
  console.log("숫자가 변동되었습니다.");
  return number;
};

const getText = (text) => {
  console.log("글자가 변동되었습니다.");
  return text;
};

const Child = ({ number, text }) => {
  const [isOpen, setIsOpen] = useState(false);

  const showNumber = getNumber(number);
  const showText = getText(text);

  return (
    <div>
      <button onClick={() => setIsOpen((prev) => !prev)} />
      <span>{showNumber}</span>
      <span>{showText}</span>
    </div>
  );
};

export default Child;
```

위 코드에서 Child 컴포넌트 내부 버튼을 클릭하면 어떻게 될까? 예상대로 props를 파라미터로 전달받아 사용하고 있는 getNumber 함수와 getText 함수 내부의 콘솔 메세지가 찍히게 된다. 즉 props와 전혀 관계가 없는 isOpen이 업데이트 되고 있는데 각 함수가 리렌더링이 발생할 때마다 동일한 연산을 반복해서 수행하고 있다. 이럴 때 useMemo를 사용하여 메모이징 할 수 있다.

```jsx
const showNumber = useMemo(() => getNumber(number), [number]);
const showText = useMemo(() => getText(text), [text]);
```

위와 같이 getNumber 호출문과 getText 호출문을 useMemo로 래핑하고 의존성 배열에 해당 함수가 사용하는 props를 넣어줌으로서 해당 props가 변하지 않는 이상 해당 함수가 컴포넌트 리렌더링 시 연산을 반복해서 수행하지 않는 것을 볼 수 있다.

<br>
<br>

# 3. useCallback 예시

간단한 useCallback 예시를 살펴보자.

```jsx
import { useEffect, useState } from "react";

const UseCallbackTest = () => {
  const [text, setText] = useState("");

  const someFunction = () => {
    console.log(`current text : ${text}`);
    return;
  };

  useEffect(() => {
    console.log("change someFunction");
  }, [someFunction]);

  return (
    <div>
      <input
        value={text}
        onChange={(event) => setText(event.currentTarget.value)}
      />
      <button onClick={someFunction} />
    </div>
  );
};

export default UseCallbackTest;
```

위 코드는 text라는 state를 가지고 있고 input에 text를 타이핑할 때 해당 text로 state가 업데이트된다. 그리고 someFunction이라는 함수가 있는데 해당 함수는 버튼이 클릭될 때 현재 text를 콘솔에 찍어주는 역할을 하고 있다. 그리고 someFunction 함수의 변화를 감지하기 위한 useEffect hook도 추가되어 있다.

위 코드를 실행시켜보면 초기 렌더링 시 useEffect 내부 콘솔 메세지가 찍히는 것을 볼 수 있다. 그 후 input에 text를 타이핑해보면 someFunction 함수의 변화가 없는데도 useEffect 내부 콘솔 메세지가 계속해서 찍히는 것을 볼 수 있다.

이 동작에서도 알 수 있듯이 input에 text를 입력할 때마다 컴포넌트 리렌더링이 발생하는데 컴포넌트가 리렌더링 될 때 내부 객체인 someFunction 함수가 초기화되며 새로 생성된다. 그렇게 되면 이전 참조 주소와 현재 참조 주소가 달라지게 되어 useEffect의 의존성 배열은 얕은 비교를 수행하여 참조가 변경되었기 때문에 해당 함수가 변경되었다고 판단하여 내부 콘솔 메세지가 찍히게 되는 것이다.

이러한 경우 useCallback을 활용하여 메모이징 할 수 있다.

```jsx
const someFunction = useCallback(() => {
  console.log(`current text : ${text}`);
  return;
}, []);
```

위와 같이 useCallback 해당 함수를 래핑하면 input 입력 시 useEffect가 트리거 되지 않는 것을 볼 수 있다. 하지만 여기서 알 수 있는 점은 만약 위와 같이 useCallback으로 래핑한 뒤 input에 ‘abc’라는 문자를 입력한 후 버튼을 클릭해 해당 함수를 실행해보면 current text는 비어있는 것을 볼 수 있다. 즉 의존성 배열이 비어있기 때문에 초기 렌더링 때 someFunction 함수가 가지고 있는 상태를 메모이징하여 사용하고 있어 메모이제이션 된 함수 내부에 text는 비어있게 되는 것이다. 여기서 알 수 있는 점은 useCallback을 활용하여 메모이징 할 때 당시 함수 상태 그대로를 메모이징 한다는 것을 알 수 있다. 함수 자체를 메모이징한다는 것이 어떠한 말인지 알 수 있는 지점이다.

또 다른 예시를 보자.

```jsx
import { useState } from "react";
import Box from "./Box";

const UseCallbackTest = () => {
  const [size, setSize] = useState(100);

  const boxStyle = () => {
    return {
      backgroundColor: "pink",
      width: `${size}px`,
      height: `${size}px`,
    };
  };

  return (
    <div>
      <input
        type="number"
        value={size}
        onChange={(event) => setSize(+event.currentTarget.value)}
      />
      <Box boxStyle={boxStyle} />
    </div>
  );
};

export default UseCallbackTest;
```

```jsx
import { useEffect, useState } from "react";

const Box = ({ boxStyle }: any) => {
  const [style, setStyle] = useState({});

  useEffect(() => {
    console.log("박스 키우기");
    setStyle(boxStyle());
  }, [boxStyle]);

  return <div style={style} />;
};

export default Box;
```

위 예시는 UseCallbackTest 내부에서 box size를 지정하는 state를 생성한 뒤 number 타입의 input을 통해 해당 state를 업데이트 시키고 있다. 그리고 boxStyle 함수 내부에서는 해당 size state의 값을 활용해 box style 객체를 return하고 있고 해당 함수를 Box 컴포넌트의 props로 넘겨주고 있다. Box 컴포넌트 내부에서는 전달받은 props를 useEffect 의존성 배열에 할당하고 useEffect 내부에서 호출하여 style state를 업데이트 시킨 뒤 해당 값으로 div 태그의 스타일을 업데이트하고 있다.

input 태그의 숫자를 증가시켜 size의 변화가 생기면 컴포넌트가 리렌더링 되고 내부 객체가 초기화되며 boxStyle 함수를 새로 생성한 뒤 해당 boxStyle 함수를 Box 컴포넌트의 props로 넘긴다. Box 컴포넌트 내부에서는 리렌더링이 발생할 때마다 전달받은 props가 변경되므로 useEffect 내부 콘솔 메세지가 찍히게 된다.

현재 까지는 문제가 없다. 이 상태에서 UseCallbackTest 컴포넌트 내부에 state를 하나 추가해보자.

```jsx
import { useState } from "react";
import Box from "./Box";

const UseCallbackTest = () => {
  const [size, setSize] = useState(100);
  const [isDark, setIsDark] = useState(false); // 추가

  const boxStyle = () => {
    return {
      backgroundColor: "pink",
      width: `${size}px`,
      height: `${size}px`,
    };
  };

  return (
    <div style={{ backgroundColor: isDark ? "black" : "white" }}>
      <input
        type="number"
        value={size}
        onChange={(event) => setSize(+event.currentTarget.value)}
      />
      <button onClick={() => setIsDark((prev) => !prev)} /> {/* 추가 */}
      <Box boxStyle={boxStyle} />
    </div>
  );
};

export default UseCallbackTest;
```

위와 같이 배경 색상을 변경하는 isDark state와 해당 state를 변경하는 button이 추가되었다. 이 상태에서 해당 버튼을 클릭하면 Box 컴포넌트 내부 useEffect 콘솔 메세지가 찍히는 것을 볼 수 있다. 해당 메세지가 찍히는 이유는 isDark state를 업데이트하고 부모 컴포넌트인 UseCallbackTest에서 리렌더링이 발생할 때 props로 전달하는 boxStyle 함수가 초기화되며 참조 주소가 변하기 때문에 해당 함수를 props로 받는 Box 컴포넌트 내부에서는 useEffect의 의존성 배열이 얕은 비교를 통해 해당 props의 참조가 변경되었다고 판단하여 계속해서 실행되는 것이다. 이러한 경우 useCallback을 통해 메모이징 하여 사용할 수 있다.

```jsx
const boxStyle = useCallback(() => {
  return {
    backgroundColor: "pink",
    width: `${size}px`,
    height: `${size}px`,
  };
}, [size]);
```

위와 같이 props로 전달하는 boxStyle을 메모이징하게 되면 다른 state에 의해 부모 컴포넌트가 리렌더링 되어도 해당 함수를 새로 생성하지 않기 때문에 동일한 참조를 가지게 된다. 그렇기 때문에 해당 함수를 props로 전달받는 Box 컴포넌트 내부에 useEffect 또한 해당 props가 변하지 않았다는 것을 알 수 있어 내부 콘솔 메세지가 찍히지 않는다.

<br>
<br>

# 4. 사용해야 하는 경우와 사용하지 말아야 하는 경우

공식 문서를 보면 useMemo와 useCallback은 꼭 필요한 상황에만 사용하라고 권고하고 있다. 그렇다면 두 hook은 언제 사용해야하고 언제 사용하면 안될까?

<br>

## 4-1. 사용해야 하는 경우

### 4-1-1. useMemo

- 값의 연산 비용이 높은 경우 리렌더링 비용 절감이 필요한 경우
- 컴포넌트 내부에서 동일한 계산을 계속해서 수행하여 최적화가 필요한 경우
- 계산 시 사용하는 특정 값이 변경 될 때만 해당 값을 다시 계산하고 싶을 때 사용
- map 혹은 filter 등을 사용하여 UI를 업데이트할 때 리렌더링 이후 동일한 참조를 사용할 가능성이 높은 경우
- 자식 컴포넌트와 관계없는 state 업데이트로 인한 부모 컴포넌트 리렌더링 발생 시 자식 컴포넌트 자체를 래핑하여 리렌더링 방지, 자식 컴포넌트는 자신이 사용하는 props를 의존성 배열에 넣어 해당 값이 변경될 때만 새로 컴포넌트가 생성될 수 있도록 함

<br>

### 4-1-2. useCallback

- 함수 자체가 매우 복잡하거나 다시 계산하는데 드는 비용이 높은 경우
- 자식 컴포넌트에 함수를 props로 넘길 때 함수의 동등성(참조 주소를 동일하게 유지)을 유지해주기 위해 사용
- 함수 내부에서 사용하는 props가 변경될 때만 해당 함수를 재생성하고 싶을 때 사용
- callback ref가 필요할 때 사용, 자식 컴포넌트의 ref를 다룰 때 forwardRef를 사용하는데 이 때 useEffect로 ref를 핸들링하면 자식 컴포넌트 내부 렌더링이 완료되기 전 ref의 값은 null이 되어 문제가 발생한다. 이럴 때 callback ref를 사용하여 해결할 수 있다. 간단하게 기본적으로 ref는 렌더링 여부를 체크할 수 없는데 useCallback을 활용하여 렌더링과 연관시켜 작업할 수 있게 되는 것이다. 즉 컴포넌트 생명주기에 바인드되던 ref를 DOM 노드의 생명주기로 바인드시키는 방식이다.

  ```jsx
  const ref = useCallback((node: any) => {
    node?.focus();
  }, []);
  ```

<br>

## 4-2. 사용하지 말아야 하는 경우

- 연산이 복잡하지 않은 값이나 함수의 경우, 연산이 복잡하지 않은 경우 메모이징하는 것이 오히려 메모리 낭비가 될 수 있다.
- 의존성 배열의 값이 자주 변화하는 경우, 자주 변하는 값이나 함수의 경우 메모이징하는 의미가 없다.
- 의존성 배열의 요소가 많은 경우, 의존성 배열의 요소가 많은 경우 자주 변하는 값이나 함수일 확률이 높기 떄문에 메모이징하는 의미가 없다.

<br>
<br>

# 5. 결론

평소 useMemo는 많이 사용해왔지만 useCallback은 그다지 많이 사용하지 않았었다. 이번 포스팅을 작성하며 useCallback 또한 매우 유용하게 사용할 수 있을 것 같다. 또한 useMemo를 사용할 때 주의하고 있었던 점은 잘하고 있었던 부분인 것 같다. 하지만 useMemo나 useCallback을 사용하며 렌더링 최적화에 큰 영향을 미치지 않는다고 생각하는 개발자 분들도 많은 것 같다. 나 또한 실제로 크게 체감하지 못했다. 그렇기 때문에 사용하지 않을 수도 있다. 하지만 미비한 차이라도 개선할 수 있다면 좋다고 생각하고 렌더단과 로직단을 분리할 때도 외부 컴포넌트로 분리하지 않고 컴포넌트 내부에서 useMemo로 래핑해서 사용하는 패턴 또한 가독성 향상에 도움이 되기 때문에 앞으로도 적극적으로 활용할 것 같다.

<br>
