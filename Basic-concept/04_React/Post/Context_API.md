# [React.js] Context API

2023년 08월 30일

<br>

## 1. Context 란?

`Context`는 react 컴포넌트 간의 어떠한 값을 공유할 수 있게 해주는 기능이다. 대부분 전역 상태 관리를 할 때 사용한다고 알고 있지만 꼭 `전역적인 값만이 아닌 react 컴포넌트에서 Props가 아닌 또 다른 방식으로 컴포넌트 간에 값을 전달하는 방법`이다. Props를 통해 컴포넌트 간의 값을 주고 받을 때 해당 값이 거치는 컴포넌트가 많아지는(깊어지는) 문제점인 Props Drilling을 해결하기 위해 사용할 수 있다.

아래는 Props Drilling의 간단한 예시이다. 최상위 컴포넌트인 ContextParent 컴포넌트에서 ContextChildrenInner 컴포넌트에 props를 전달하기 위해 해당 value를 사용하지 않는 ContextChildrenOuter 컴포넌트를 거쳐 해당 props를 전달하고 있다. 해당 예시는 depth가 2단계 정도로 어느 정도 허용되는 경우이지만 심각한 경우는 많은 문제를 초래할 수 있다.

```tsx
// ContextParent.tsx
import ContextChildrenOuter from "./contextChildrenOuter";

const ContextParent = () => {
  const props = "Hello World";

  return <ContextChildrenOuter value={props} />;
};

export default ContextParent;
```

```tsx
// ContextChildrenOuter.tsx
import ContextChildrenInner from "./contextChildrenInner";

const ContextChildrenOuter = ({ value }: any) => {
  return <ContextChildrenInner value={value} />;
};

export default ContextChildrenOuter;
```

```tsx
// ContextChildrenInner.tsx
const ContextChildrenInner = ({ value }: any) => {
  return <div>{value}</div>;
};

export default ContextChildrenInner;
```

<br>
<br>

## 2. Context 사용법

### 2-1. 기본 사용법

1에서 사용한 예시를 `Context`를 사용해서 바꾸어보자.

```tsx
import { createContext } from "react";
```

`Context` 는 리액트 패키지에서 `createContext` 라는 함수를 불러와서 만들 수 있다.

```jsx
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
```

`createContext` 함수로 Context를 생성한다. createContext가 리턴하는 객체에는 `Provider`라는 컴포넌트를 가지고 있다. 이 `Provider`로 값을 공유하고자 하는 최상위 부모 컴포넌트를 감싼 뒤 공유하고자 하는 값을 `value`로 넘겨준다.

```jsx
// ContextChildrenInner.tsx
import { useContext } from "react";
import { MyContext } from "./contextParent";

const ContextChildrenInner = () => {
  const value = useContext(MyContext);

  return <div>{value}</div>;
};

export default ContextChildrenInner;
```

해당 값을 사용하기 위해 `useContext`라는 hook을 사용할 수 있다. useContext의 인자로는 `createContext 함수로 생성한 Context`를 인자로 넘겨주면 된다.

```tsx
// ContextChildrenOuter.tsx
import ContextChildrenInner from "./contextChildrenInner";

const ContextChildrenOuter = () => {
  return <ContextChildrenInner />;
};

export default ContextChildrenOuter;
```

위와 같이 작성하면 1에서 작성한 것과 같이 해당 value를 사용하지 않는 컴포넌트는 불필요하게 props를 전달받을 필요가 없다. 즉 react의 데이터 흐름은 하향식으로 흐르는데 하향식이 아닌 곧바로 사용할 수 있어 Props Drilling 문제를 해결할 수 있다.

<br>

### 2-2. 커스텀 훅 사용

추가로 위와 같이 한 곳에서 사용하는 것이 아닌 해당 Context가 여러 곳에서 사용된다면 `Custom hook`을 만들어서 사용하는 것은 좋은 방법이 될 수 있다.

```tsx
// MyContext.tsx
import { ReactNode, createContext, useContext } from "react";

interface MyContextProviderProps {
  children: ReactNode;
}

const MyContext = createContext("");

const useMyContext = () => {
  return useContext(MyContext);
};

const MyContextProvider = ({ children }: MyContextProviderProps) => {
  const props = "Hello World";

  return <MyContext.Provider value={props}>{children}</MyContext.Provider>;
};

export default MyContextProvider;
export { useMyContext };
```

우선 위와 같이 Custom hook을 생성한다. Provider 컴포넌트를 리턴하는 `MyContextProvider` 컴포넌트와 `useContext`를 사용하여 해당 Context의 value를 반환하는 함수인 `useMyContext`를 생성하여 export 하였다.

```tsx
// ContextParent.tsx
import ContextChildrenOuter from "./contextChildrenOuter";
import MyContextProvider from "./MyContext";

const ContextParent = () => {
  return (
    <MyContextProvider>
      <ContextChildrenOuter />
    </MyContextProvider>
  );
};

export default ContextParent;
```

그 후 Custom hook 내부에서 생성한 `Provider`를 import 하여 값을 공유하고자 하는 컴포넌트의 최상위 컴포넌트를 감싸준다.

```tsx
// ContextChildrenInner.tsx
import { useMyContext } from "./MyContext";

const ContextChildrenInner = () => {
  const value = useMyContext();

  return <div>{value}</div>;
};

export default ContextChildrenInner;
```

실제 값을 사용하기 위해서 Custom hook 내부에서 생성한 value를 리턴하는 useMyContext를 import 하여 변수에 할당한 뒤 사용한다.

```tsx
// MyContext.tsx
import { ReactNode, createContext, useContext } from "react";

interface MyContextProviderProps {
  children: ReactNode;
}

const MyContext = createContext<string | undefined>(undefined);

const useMyContext = () => {
  const value = useContext(MyContext);

  if (value === undefined) {
    throw new Error("useMyContext should be used within MyContext.Provider");
  }

  return value;
};

const MyContextProvider = ({ children }: MyContextProviderProps) => {
  const props = "Hello World";

  return <MyContext.Provider value={props}>{children}</MyContext.Provider>;
};

export default MyContextProvider;
export { useMyContext };
```

추가로 위와 같이 작성 후 최상위 컴포넌트에 `Provider`로 감싸는 단계를 빼먹는 경우 `useMyContext`를 통해 해당 Context의 value를 사용할 때 업데이트 되지 않은 최초 값인 빈 값을 얻게 된다. 이럴 때 해당 Context의 value를 리턴하는 `useMyContext` 내부에 if 문을 통한 에러 핸들링을 통해 개발자가 에러를 캐치할 수 있도록 변경해줄 수 있다.

<br>

### 2-3. Context 에서 상태 관리가 필요한 경우

이번에는 Context 에서 유동적인 값을 다뤄야 할 때는 어떻게 해야 하는지 알아보자.

```tsx
// ContextParent.tsx
import Value from "./Value";
import Buttons from "./Buttons";

const ContextParent = () => {
  return (
    <div>
      <Value />
      <Buttons />
    </div>
  );
};

export default ContextParent;
```

```tsx
// Value.tsx
const Value = () => {
  return <h1>1</h1>;
};

export default Value;
```

```tsx
// Buttons.tsx
const Buttons = () => {
  return (
    <div>
      <button>+</button>
      <button>-</button>
    </div>
  );
};

export default Buttons;
```

위와 같이 버튼을 눌렀을 때 해당 숫자가 카운트되는 기능이 있다. 이 때 숫자를 보여주는 UI와 숫자에 변화를 주는 버튼 UI가 완전히 분리되어 있다고 했을 때 이를 Props로 전달하는 것이 아닌 Context로 구현해보자.

```tsx
// CounterProvider.tsx
import { ReactNode, createContext, useContext, useState } from "react";

interface CounterProviderProps {
  children: ReactNode;
}

interface CounterContextType {
  count: number;
  setCount: React.Dispatch<React.SetStateAction<number>>;
}

const CounterContext = createContext<CounterContextType | undefined>(undefined);

const useCounterContext = () => {
  const value = useContext(CounterContext);

  if (value === undefined) {
    throw new Error("ChildComponent must be used within MyContext.Provider");
  }

  return value;
};

const CounterProvider = ({ children }: CounterProviderProps) => {
  const [count, setCount] = useState(0);

  return (
    <CounterContext.Provider value={{ count, setCount }}>
      {children}
    </CounterContext.Provider>
  );
};

export default CounterProvider;
export { useCounterContext };
```

우선 위와 같이 Custom hook 먼저 작성해준다. `CounterContext` 변수에 createContext로 생성한 Context 객체를 할당하였다. 이 때 초기 값은 `undefined`로 할당하였다. 왜냐하면 Provider는 필수적으로 감싸주어야 하는데 `감싸지 않은 경우를 캐치`하여 에러를 출력하기 위함이다. 또한 createContext 타입으로 `union 타입`을 사용해주었다. union 타입을 지정한 이유는 실제 `Provider에 value로 전달되는 값의 타입과 초기 값 undefined의 타입을 함께 지정`해주기 위해 사용하였다. 이 때 실제 Provider에 전달되는 값은 useState로 생성할 동적인 값 state와 동적인 값을 업데이트 시킬 setState를 전달할 것이다. 그렇기 때문에 interface 타입을 사용하여 state와 setState의 타입을 지정하여 createContext 타입으로 지정하였다. 그 후 Provider 내부에서는 useState를 사용하여 동적인 값 count와 업데이트 시킬 setCount를 생성하고 해당 값을 Provider value에 객체 형태로 넘겨주었다.

```tsx
// ContextParent.tsx
import Value from "./Value";
import Buttons from "./Buttons";
import CounterProvider from "./CounterContext";

const ContextParent = () => {
  return (
    <CounterProvider>
      <Value />
      <Buttons />
    </CounterProvider>
  );
};

export default ContextParent;
```

Custom hook 작성 완료 후 해당 Context를 사용 할 컴포넌트 혹은 최상위 컴포넌트에서 Provider 컴포넌트로 감싸주어 해당 Context의 value를 사용할 수 있도록 한다.

```tsx
// Buttons.tsx
import { useCounterContext } from "./CounterContext";

const Buttons = () => {
  const { setCount } = useCounterContext();

  return (
    <div>
      <button onClick={() => setCount((prev) => prev + 1)}>+</button>
      <button onClick={() => setCount((prev) => prev - 1)}>-</button>
    </div>
  );
};

export default Buttons;
```

그 후 Buttons 컴포넌트 내부에서 버튼을 클릭하면 값이 업데이트 될 수 있도록 Custom hook 내부에서 작성한 useCounterContext 함수를 가져와 useCounterContext 함수가 리턴하는 객체 내부에 setCount를 사용하여 해당 값이 업데이트 될 수 있도록 한다.

```tsx
// Value.tsx
import { useCounterContext } from "./CounterContext";

const Value = () => {
  const { count } = useCounterContext();

  return <h1>{count}</h1>;
};

export default Value;
```

마지막으로 Value 컴포넌트에서 동적인 값을 보여주기 위해 Custom hook 내부에서 작성한 useCounterContext 함수를 가져와 useCounterContext 함수가 리턴하는 객체 내부에 count를 사용하여 해당 값을 사용해 UI를 띄워줄 수 있다.

추가로 위와 같이 Buttons 내부에서 setState를 할 수 있지만 Provider 내부에서 한번에 처리도 가능하다.

```tsx
import { ReactNode, createContext, useContext, useMemo, useState } from "react";

interface CounterProviderProps {
  children: ReactNode;
}

interface ActionsType {
  increase: () => void;
  decrease: () => void;
}

interface CounterContextType {
  count: number;
  actions: ActionsType;
}

const CounterContext = createContext<CounterContextType | undefined>(undefined);

const useCounterContext = () => {
  const value = useContext(CounterContext);

  if (value === undefined) {
    throw new Error("ChildComponent must be used within MyContext.Provider");
  }

  return value;
};

const CounterProvider = ({ children }: CounterProviderProps) => {
  const [count, setCount] = useState(0);

  const actions = useMemo(
    () => ({
      increase: () => {
        setCount((prev) => prev + 1);
      },
      decrease: () => {
        setCount((prev) => prev - 1);
      },
    }),
    []
  );

  const value = useMemo(() => ({ count, actions }), [count, actions]);

  return (
    <CounterContext.Provider value={value}>{children}</CounterContext.Provider>
  );
};

export default CounterProvider;
export { useCounterContext };
```

기존 CounterProvider와 다른 점은 value로 넘겨주는 인자 중 setCount 대신 `actions`를 넘겨주고 있다. actions 객체는 count를 증가시키거나 감소시키는 setCount 함수를 value로 가지고 있는 객체이다. 이 객체 자체를 넘겨주고 있는 것이다. 이 때 useMemo를 사용한 이유는 리렌더링 될 때마다 함수를 새로 만드는게 아니라 처음에 한번 만들고 그 이후에 재사용할 수 있도록 useMemo로 감싸주었다. 또 value도 바로 넘기지 않고 useMemo로 한번 더 감싸고 있는데 useMemo로 감싸지 않으면 CounterProvider가 리렌더링이 될 때마다 새로운 객체를 만들기 때문에 useCounterContext 를 사용하는 컴포넌트 쪽에서 Context의 값이 바뀐 것으로 간주하게 되어 낭비 렌더링이 발생하게 된다.

```tsx
import { useCounterContext } from "./CounterContext";

const Buttons = () => {
  const { actions } = useCounterContext();

  return (
    <div>
      <button onClick={actions.increase}>+</button>
      <button onClick={actions.decrease}>-</button>
    </div>
  );
};

export default Buttons;
```

이후 Buttons 버튼 컴포넌트 내부에서는 setCount 함수를 value로 가지고 있는 객체를 사용하기만 하면 된다.

<br>

### 2-4. 값과 업데이트 함수를 두개의 Context로 분리하기

만약 Context에서 관리하는 상태가 빈번하게 업데이트 되지 않는다면 방금 작성한 코드만으로도 충분하다. 하지만, 만약에 상태가 빈번하게 업데이트 된다면, 성능적으로 좋지 않다.

실제로 변화가 반영되는 곳은 `Value` 컴포넌트뿐인데, `Buttons` 컴포넌트도 리렌더링되기 때문이다.

왜 그럴까? 우리가 비록 `value`를 만드는 과정에서 `useMemo`로 감싸주었긴 하지만, 어쨌든 `counter`가 바뀔 때 마다 새로운 객체를 만들어서 반환하고 있고 `useContext`에선 이를 감지하여 리렌더링을 하기 때문이다.

```tsx
// Value.tsx
import { useCounterContext } from "./CounterContext";

const Value = () => {
  console.log("Value"); // 컴포넌트 렌더링 체크
  const { count } = useCounterContext();

  return <h1>{count}</h1>;
};

export default Value;
```

```tsx
// Buttons.tsx
import { useCounterContext } from "./CounterContext";

const Buttons = () => {
  console.log("Buttons"); // 컴포넌트 렌더링 체크
  const { actions } = useCounterContext();

  return (
    <div>
      <button onClick={actions.increase}>+</button>
      <button onClick={actions.decrease}>-</button>
    </div>
  );
};
```

위와 같이 `console.log`를 추가해서 컴포넌트가 렌더링 되는지 확인해보자. 그러면 상태 변화 시 Value 컴포넌트와 Buttons 컴포넌트 모두 리렌더링 되는 것을 확인할 수 있다.

이것을 고치는 방법은 간단하다. 바로 Context를 분리하는 것이다.

```tsx
// CounterProvider.tsx
import { ReactNode, createContext, useContext, useMemo, useState } from "react";

interface CounterProviderProps {
  children: ReactNode;
}

interface ActionsType {
  increase: () => void;
  decrease: () => void;
}

const CounterContext = createContext<number | undefined>(undefined);
const ActionsContext = createContext<ActionsType | undefined>(undefined);

const useCounterContext = () => {
  const value = useContext(CounterContext);

  if (value === undefined) {
    throw new Error(
      "ChildComponent must be used within CounterContext.Provider"
    );
  }

  return value;
};

const useActionsContext = () => {
  const value = useContext(ActionsContext);

  if (value === undefined) {
    throw new Error(
      "ChildComponent must be used within ActionsContext.Provider"
    );
  }

  return value;
};

const CounterProvider = ({ children }: CounterProviderProps) => {
  const [count, setCount] = useState(0);

  const actions = useMemo(
    () => ({
      increase: () => {
        setCount((prev) => prev + 1);
      },
      decrease: () => {
        setCount((prev) => prev - 1);
      },
    }),
    []
  );

  return (
    <CounterContext.Provider value={count}>
      <ActionsContext.Provider value={actions}>
        {children}
      </ActionsContext.Provider>
    </CounterContext.Provider>
  );
};

export default CounterProvider;
export { useCounterContext, useActionsContext };
```

기존 하나로 사용하던 Provider를 `CounterContext`와 `ActionsContext`를 분리하였다. 그 후 Custom hook 또한 useCounterContext와 useActionsContext로 분리하였다. 그 후 Value 컴포넌트에서는 useCounterContext를 사용하고 Buttons 컴포넌트에서는 useActionsContext를 사용하였다. 이렇게 수정한 뒤 렌더링을 체크해보면 버튼을 클릭하여 상태를 업데이트 시킬 때 Value 컴포넌트만 리렌더링 되는 것을 확인할 수 있다.

<br>

### 2-5. Context가 꼭 전역적이어야 한다는 생각을 버리자

Context에서 다루는 값은 꼭 전역적일 필요가 없습니다. Context는 재사용성이 높은 컴포넌트를 만들때도 매우 유용하다. 예를 들어 클릭 시 버튼이 활성화되는 기능을 구현한다고 해보자.

```tsx
// Item.jsx
const activeStyle = {
  backgroundColor: "black",
  color: "white",
};

const style = {
  cursor: "pointer",
  padding: "1rem",
};

const Item = ({ active, children, onClick }) => {
  return (
    <div
      style={active ? { ...style, ...activeStyle } : style}
      onClick={onClick}
    >
      {children}
    </div>
  );
};

export default Item;
```

```tsx
// ItemGroup.jsx
import { useState } from "react";
import Item from "./Item";

const ItemGroup = () => {
  const [activeId, setActiveId] = useState(1);

  return (
    <div>
      <Item active={activeId === 1} onClick={() => setActiveId(1)}>
        Hello
      </Item>
      <Item active={activeId === 2} onClick={() => setActiveId(2)}>
        World
      </Item>
      <Item active={activeId === 3} onClick={() => setActiveId(3)}>
        React
      </Item>
    </div>
  );
};

export default ItemGroup;
```

![ReactJs_Context_API_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/bf7841db-ec07-4dc3-9958-c761550770a2)

위 코드를 Context를 활용하여 수정해보자

```tsx
// ItemGroupProvider.jsx
import { createContext, useMemo, useContext } from "react";

const ItemGroupContext = createContext();

const useItemGroupContext = () => {
  const value = useContext(ItemGroupContext);

  if (value === undefined) {
    throw new Error("Item component should be used within ItemGroup");
  }

  return value;
};

const ItemGroupProvider = ({ children, activeId, onSelect }) => {
  const value = useMemo(
    () => ({
      activeId,
      onSelect,
    }),
    [activeId, onSelect]
  );

  return (
    <ItemGroupContext.Provider value={value}>
      {children}
    </ItemGroupContext.Provider>
  );
};

export default ItemGroupProvider;
export { useItemGroupContext };
```

`ItemGroupProvider`를 생성한다. 이 때 활성화 된 현재 활성화 된 id를 가져오는 파라미터 `activeId`와 클릭한 아이템의 id로 상태를 업데이트 시키는 setState인 `onSelect`를 파라미터로 받아온다.

```tsx
// Item.jsx
import { useMemo } from "react";
import { useItemGroupContext } from "./ItemGroupProvider";

const activeStyle = {
  backgroundColor: "black",
  color: "white",
};

const style = {
  cursor: "pointer",
  padding: "1rem",
};

const Item = ({ children, id }) => {
  const { activeId, onSelect } = useItemGroupContext();

  const dynamicStyle = useMemo(() => {
    if (activeId === id) {
      return { ...style, ...activeStyle };
    }

    return style;
  }, [activeId, id]);
  const onClick = () => onSelect(id);

  return (
    <div style={dynamicStyle} onClick={onClick}>
      {children}
    </div>
  );
};

export default Item;
```

useItemGroupContext 함수를 가져와 useItemGroupContext가 출력하는 activeId, onSelect를 가져온다. 그 후 파라미터로 받아오는 현재 아이템의 id와 비교하여 activeId와 같은 경우 동적 스타일링을 적용시키고 각 아이템들을 클릭했을 때는 onSelect를 트리거하여 현재 아이템의 id로 상태가 업데이트 되도록 한다.

```tsx
// ItemGroup.jsx
import { useState } from "react";
import Item from "./Item";
import ItemGroupProvider from "./ItemGroupProvider";

const ItemGroup = () => {
  const [activeId, setActiveId] = useState(1);
  const [anotherActiveId, setAnotherActiveId] = useState(4);

  return (
    <div>
      <ItemGroupProvider activeId={activeId} onSelect={setActiveId}>
        <Item id={1}>Hello</Item>
        <Item id={2}>World</Item>
        <Item id={3}>React</Item>
      </ItemGroupProvider>
      <hr />
      <ItemGroupProvider
        activeId={anotherActiveId}
        onSelect={setAnotherActiveId}
      >
        <Item id={4}>Bye</Item>
        <Item id={5}>World</Item>
        <Item id={6}>Context</Item>
      </ItemGroupProvider>
    </div>
  );
};

export default ItemGroup;
```

최종적으로 ItemGroupProvider 컴포넌트와 Item 컴포넌트를 활용하여 위와 같이 사용할 수 있다.

결과는 아래와 같다.

![ReactJs_Context_API_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/83183b94-d017-4161-beac-5138ca446cac)

필요한 값과 함수를 매번 Props로 넣어주는 대신, `ItemGroupProvider` 이라는 Provider 컴포넌트를 만들어서 해당 컴포넌트에만 한번 넣어주고 `Item` 에서 Context를 읽어와서 값을 사용하도록 만들었다.

작성해야 할 전체적인 코드는 조금 늘어났지만, `Item` 코드를 사용하는 쪽에서는 훨씬 가독성 높고 편하게 작성할 수 있고 재사용성 또한 좋아졌다.

이렇게 Context 를 꼭 전역적인 값을 위해서만 쓰는게 아니라, Props가 아닌 또 다른 방식으로 데이터를 전달하는 것이라는 접근을 하여 사용한다면 다양한 상황에 유용하게 쓸 수 있다.

<br>

### 2-6. Context.Consumer

```tsx
<MyContext.Consumer>
  {value => /* context 값을 이용한 렌더링 */}
</MyContext.Consumer>
```

Context 객체의 `Consumer` 컴포넌트는 context 변화를 구독하는 컴포넌트이다. context의 자식은 함수(컴포넌트)이어야 한다. 이 함수(컴포넌트)가 가지는 context 값은 가장 가까운 provider의 값이다. 만약 상위 provider가 없다면 `createContext()`에서 정의한 `defaultValue`를 가진다.

```tsx
<ThemeContext.Consumer>
  {(theme) => (
    <UserContext.Consumer>
      {(user) => <ProfilePage user={user} theme={theme} />}
    </UserContext.Consumer>
  )}
</ThemeContext.Consumer>
```

만약 여러 컴포넌트를 구독하려면 아래와 같이 Consumer 내부에 또다른 Consumer를 정의하는 방법으로 context를 내려줘야한다. react에서는 둘 이상의 context가 중첩되는 경우 한번에 prop을 내리는 방법을 고안하라 추천한다.

<br>

### 2-7. 전역 상태 관리 라이브러리는 언제 써야 할까?

Redux, MobX, Recoil, Jotai, Zustand 등의 전역 상태 관리 라이브러리를 때때로 Context와 비교하기도 한다. 하지만 `상태 관리 라이브러리`와 `Context`는 완전히 별개의 개념임을 잘 이해해야한다

Context는 전역 상태 관리를 할 수 있는 수단일 뿐이고, 상태 관리 라이브러리는 상태 관리를 더욱 편하고, 효율적으로 할 수 있게 해주는 기능들을 제공해주는 도구이다.

예를 들어, Redux의 경우에는 액션과 리듀서라는 개념을 사용하여 상태 업데이트 로직을 컴포넌트 밖으로 분리 할 수 있게 해주며, 상태가 업데이트 될 때 실제로 의존하는 값이 바뀔 때만 컴포넌트가 리렌더링 되도록 최적화를 해줍니다. 만약 Context를 쓴다면, 각기 다른 상태마다 새롭게 Context를 만들어주어야 하는데, 이 과정을 생략할 수 있기에 편리하다.

MobX의 경우엔 Redux와 마찬가지로 상태 업데이트 로직을 컴포넌트 밖으로 분리할 수 있게 해주고, 함수형 리액티브 프로그래밍 방식을 도입하여 mutable한 상태가 리액트에서도 잘 보여지게 해주고 상태 업데이트 로직을 더욱 편하게 작성할 수 있게 해주며 최적화도 잘 해준다.

Recoil, Jotai, Zustand의 경우엔 Context를 일일이 만드는 과정을 생략하고 Hook 기반으로 아주 편하게 전역 상태 관리를 할 수 있게 해주며 최적화 기능도 제공한다.

전역 상태 라이브러리는 결국 상태 관리를 조금 더 쉽게 하기 위해서 사용하는 것이며 취향에 따라 선택해서 사용하면 된다.

<br>
<br>

# 3. 참고 URL

- https://velog.io/@velopert/react-context-tutorial
- [https://kyounghwan01.github.io/blog/React/react-context-api/#예시](https://kyounghwan01.github.io/blog/React/react-context-api/#%E1%84%8B%E1%85%A8%E1%84%89%E1%85%B5)

<br>
