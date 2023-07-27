# **[React.js] Headless UI 라이브러리**

2023년 07월 27일

<br>

## **1. Headless란?**

`Headless`는 웹 개발에서 주로 백엔드와 프론트엔드를 분리하는 개념이다. 즉 프론트엔드 로직과 백엔드 로직을 분리하여 프론트엔드는 사용자 인터페이스만을 담당하고 백엔드는 데이터 로직을 처리하는 것을 말한다.

<br>
<br>

## **2. Headless UI**

프론트엔드 웹 개발을 하다보면 생산성 향상을 위해 `UI 라이브러리`를 사용하고는 한다. 일반적인 `Component 기반 UI 라이브러리`는 개발자가 해당 컴포넌트를 바로 사용할 수 있도록 고유의 스타일이 적용되어있는데 거의 모든 사용되는 서비스 디자인에 맞게 커스텀이 필요하게 된다. 하지만 커스텀하는 과정 중 한계에 부딪히는 경우가 발생할 수 있고 커스텀이 까다로운 경우도 발생할 수 있다. 이러한 경우 `Headless UI` 라이브러리를 사용할 수 있다.

<br>

### **2-1. Component 기반 UI 라이브러리**

`Component 기반 UI 라이브러리`는 기능과 스타일이 존재하는 라이브러리를 말하며, 대표적으로 [Material UI](https://mui.com/), [Ant Design](https://ant.design/)가 있다. 디자인이 그렇게 중요하지 않고, 커스텀할 곳이 많지 않다면 `Component 기반 UI 라이브러리`를 사용하면 된다.

<br>

#### **2-1-1. Component 기반 UI 장단점**

**[ 장점 ]**

- 바로 사용할 수 있는 마크업과 스타일이 존재
- 설정이 거의 필요 없음

**[ 단점 ]**

- 마크업을 자유롭게 할 수 없음
- 스타일은 대부분 라이브러리에 있는 테마 기반으로만 변경할 수 있어 한정적임
- 큰 번들 사이즈

<br>

### **2-2. Headless UI 라이브러리**

`Headless UI 라이브러리`는 기능은 있지만 스타일이 없는 라이브러리로, [Headless UI](https://headlessui.dev/), [Radix UI](https://www.radix-ui.com/), [Reach UI](https://github.com/reach/reach-ui) 등이 있다. 만약 반응형에 따라 디자인이 달라지고, 기능 변경이나 추가가 많이 발생한다면 `Headless UI 라이브러리`가 유지보수에 더 좋을 수 있다.

<br>

#### **2-1-1. Headless UI 라이브러리 장단점**

**[ 장점 ]**

- 마크업과 스타일을 완벽하게 제어 가능
- 관심사의 분리로 인한 유지보수 용이
- 모든 스타일링 패턴 지원(ex. CSS, CSS-in-JS, UI 라이브러리 등)
- 작은 번들 사이즈

**[ 단점 ]**

- 추가 설정이 필요함
- 마크업, 스타일 혹은 테마 모두 지원되지 않음

<br>
<br>

## **3. Headless Component 만들기**

하지만 아직 `Headless UI 라이브러리`에는 컴포넌트의 종류가 상대적으로 적다. 그래서 바로 사용해야 하는 컴포넌트가 없다면 만들어야 한다. `Headless Component`를 만들기 위한 원칙은 아래와 같다.

- 만드려는 컴포넌트에 어떤 메서드가 있는지를 먼저 결정하기보다, 그 컴포넌트가 무엇을 수행할 수 있는지부터 결정해야 한다.

- 그리고 사용자가 사용할 수 있는 기능들과 방법을 제공해야 한다.

- 이후에 그 기능을 어떻게 수행할 지 구현하면 된다.

아래와 같은 체크박스 컴포넌트가 있다고 가정해보자.

```tsx
// Checkbox.tsx
type CheckboxProps = {
  label: string;
  isChecked: boolean;
  onChange: () => void;
};

const Checkbox = ({ label, isChecked, onChange }: CheckboxProps) => {
  return (
    <label>
      <input type="checkbox" checked={isChecked} onChange={onChange} />
      <span>{label}</span>
    </label>
  );
};

export default Checkbox;
```

```tsx
// App.tsx
export default function App() {
  const [isChecked, setIsChecked] = useState(false);
  return (
    <Checkbox
      label="체크박스 만들기"
      isChecked={isChecked}
      onChange={() => setIsChecked(!isChecked)}
    />
  );
}
```

![Headless_UI_라이브러리_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/451179a4-9766-4e92-a35b-22c031fb3335)

위 코드는 Checkbox 컴포넌트를 재사용하기 위해 Props를 받아 사용하는 예시이다. 하지만 만약 특정 페이지에서 컬러가 다르게 적용되거나 버튼의 위치가 달라지거나 하면 어떻게 될까? Props를 추가해서 처리할 수 있겠지만 유지보수가 어려워질 수 있다. 이럴 때 유지보수가 용이하도록 `Headless Component`로 만들면 된다. 위에 `Headless Component`를 만드는 원칙을 관점으로 생각해보자.

- 컴포넌트가 무엇을 수행할 수 있는지부터 결정해야 한다.
  - 상태에 대한 라벨(설명)이 있다.
  - 마우스로 체크박스나 라벨을 클릭할 수 있다.
  - 체크가 안 된 상태라면 박스가 비어있고, 체크가 된 상태면 박스가 ✓ 아이콘이 생긴다.
- 그리고 사용자가 사용할 수 있는 기능들과 방법을 제공해야 한다.
  - 사용자는 Checkbox 컴포넌트를 마우스로 클릭할 수 있다. 사용자는 그저 체크박스 컴포넌트를 클릭할 뿐, 컴포넌트 내부가 어떻게 구현되어 있는지는 알 수 없고 알 필요도 없다.

`Headless Component`를 만드는 방식은 다양한데, 그 중 세 가지 방법을 소개해보려 한다.

### **3-1. Compound Component (with** Context API)\*\*

Material UI, Reach UI등 많은 UI 라이브러리가 `Compound Component`를 사용한다.
`Compound Component`란 같이 사용되는 컴포넌트들의 상태(state) 값을 공유할 수 있게 만들어주는 패턴이다. 코드로 한 번 알아보자.

```tsx
// CheckboxWrapper.tsx
import * as React from "react";

type CheckboxContextProps = {
  id: string;
  isChecked: boolean;
  onChange: () => void;
};

type CheckboxProps = CheckboxContextProps & React.PropsWithChildren<{}>;

const CheckboxContext = React.createContext<CheckboxContextProps>({
  id: "",
  isChecked: false,
  onChange: () => {},
});

const CheckboxWrapper = ({
  id,
  isChecked,
  onChange,
  children,
}: CheckboxProps) => {
  const value = {
    id,
    isChecked,
    onChange,
  };
  return (
    <CheckboxContext.Provider value={value}>
      {children}
    </CheckboxContext.Provider>
  );
};

const useCheckboxContext = () => {
  const context = React.useContext(CheckboxContext);
  return context;
};

const Checkbox = ({ ...props }) => {
  const { id, isChecked, onChange } = useCheckboxContext();
  return (
    <input
      type="checkbox"
      id={id}
      checked={isChecked}
      onChange={onChange}
      {...props}
    />
  );
};

const Label = ({ children, ...props }: React.PropsWithChildren<{}>) => {
  const { id } = useCheckboxContext();
  return (
    <label htmlFor={id} {...props}>
      {children}
    </label>
  );
};

CheckboxWrapper.Checkbox = Checkbox;
CheckboxWrapper.Label = Label;

export default CheckboxWrapper;
```

```tsx
// App.tsx
import CheckboxWrapper from "./CheckboxWrapper";

export default function App() {
  const [isChecked, setIsChecked] = useState(false);
  return (
    <CheckboxWrapper
      id="checkbox-1"
      isChecked={isChecked}
      onChange={() => setIsChecked(!isChecked)}
    >
      <CheckboxWrapper.Checkbox />
      <CheckboxWrapper.Label>체크박스 만들기</CheckboxWrapper.Label>
    </CheckboxWrapper>
  );
}
```

컴포넌트 내부에서 state를 공유하기 위해 Context API를 사용해서 처음에 작성해야 하는 코드가 꽤 많다.

하지만 컴포넌트를 사용하는 곳에서는 `<CheckboxWrapper />` 하위에 어떤 컴포넌트가 있는지 볼 수 있고, 위치도 자유롭게 수정 가능하다.

### **3-2. Function as Child Component**

`Function as Child Component`는 자식에 어떤 것이 들어올지 예상할 수 없기 때문에 `children` prop으로 받아 그대로 전달하는 것이다.

```tsx
// CheckboxHeadless.ts
type CheckboxHeadlessProps = {
  isChecked: boolean;
  onChange: () => void;
};

const CheckboxHeadless = (props: {
  children: (args: CheckboxHeadlessProps) => JSX.Element;
}) => {
  const [isChecked, setIsChecked] = useState(false);

  if (!props.children || typeof props.children !== "function") return null;

  return props.children({
    isChecked,
    onChange: () => setIsChecked(!isChecked),
  });
};

export default CheckboxHeadless;
```

```tsx
// App.tsx
import CheckboxHeadless from "./CheckboxHeadless";

export default function App() {
  return (
    <CheckboxHeadless>
      {({ isChecked, onChange }) => {
        return (
          <label>
            <input type="checkbox" checked={isChecked} onChange={onChange} />
            <span>체크박스</span>
          </label>
        );
      }}
    </CheckboxHeadless>
  );
}
```

`Compound Component`보다 작성해야 하는 코드량이 훨씬 적다. 사용하려는 state 값을 위에서 따로 선언할 필요가 없어, 다른 컴포넌트에 해당 state를 실수로 넣을 일이 적어진다. 그리고 관련된 코드가 한 곳에 모여 있어 읽기 편하다. 하지만 다른 곳에서 해당 state를 공유할 경우, `CheckboxHeadless`가 감싸야 할 코드량이 많아지는 단점이 있다.

### **3-3. Custom hooks**

React를 사용해본 사람이라면 가장 익숙할 법한 `Custom hooks`이다.

```tsx
// useCheckbox.ts
import { useState } from "react";

export const useCheckbox = () => {
  const [isChecked, setIsChecked] = useState(false);

  return {
    isChecked,
    onChange: () => setIsChecked(!isChecked),
  };
};
```

```tsx
// App.tsx
import { useCheckbox } from "./useCheckbox";

export default function App() {
  const { isChecked, onChange } = useCheckbox();
  return (
    <label>
      <input type="checkbox" checked={isChecked} onChange={onChange} />
      <span>체크박스 만들기</span>
    </label>
  );
}
```

위의 두 방식보다 간단하고 직관적이다. 하지만 state 값을 사용되어야 하는 Checkbox 컴포넌트가 아니라 다른 곳에 작성할 실수가 발생할 수 있다.
