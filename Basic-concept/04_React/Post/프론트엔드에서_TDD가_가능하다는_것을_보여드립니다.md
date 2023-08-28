# **[React.js] 프론트엔드에서 TDD가 가능하다는 것을 보여드립니다.**

2023년 08월 26일

<br>

## **0. 포스트 개요**

[[A5] 프론트엔드에서 TDD가 가능하다는 것을 보여드립니다.](https://youtu.be/L1dtkLeIz-M)

- Frontend Conference 2020 최수형 개발자님의 TDD 발표 영상을 보며 작성한 포스팅입니다.
- 발표자료 : https://drive.google.com/file/d/1658E_OFq-Iq4f2kCRKxL-afUz3NVmzWL/view
- 데모코드 : https://github.com/megaptera-kr/frontend-tdd-feconf2020

<br>
<br>

## **1. TDD를 하지 않는 이유**

- 대부분 다른 개발 일정에 의해 우선 순위가 미루어 진다.
- 즉 `시간 소모`의 이유로 TDD를 하지 않는다.

<br>
<br>

## **2. TDD란**

- `TDD(Test Driven Development)`
- Kent Beck의 `TDD By Example`이라는 책은 TDD를 잘 정리해놓았다.
- TDD의 궁극적 목표는 `Clean Code that works`, 말 그대로 작동하는 깔끔한 코드가 목표이다.
- TDD를 다르게 얘기하면 `Test First Programming`이라고 한다. 테스트를 먼저 작성하는 프로그래밍 방식을 말한다. TDD의 사이클은 아래 이미지와 같이 Red, Green, Refactor 사이클을 도는데 처음에 `실패`하고, 빠르게 `통과` 시키고, 중복을 제거하면서 `개선`하는 개발 사이클을 가진다.

  ![Reactjs_프론트엔드에서_TDD가_가능하다는_것을_보여드립니다_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/037ce499-463a-4a47-9463-0e2fc441dfb4)

<br>
<br>

## **3. TDD가 어려운 이유**

- 코드 자체가 Testable 하지 않기 때문이다. 해결법은 간단하다. 코드를 `Testable Code`로 작성해야한다.
- Testable 하게 만드는 방법, 가장 중요한 부분은 `관심사의 분리 (Separation of Concerns)`이다. 이 원칙을 지키지 않을 경우 해당 서비스의 코드는 `거대한 진흙 덩어리(Big Ball of Mud)`로 발전하게 된다.

<br>
<br>

## **4. TDD 실습**

### **4-1. To Do List 테스트 (03:30~)**

시연 환경은 React이며 To-do 서비스를 TDD로 작성해본다. 테스트 전 일단 jest 설치를 해준다. 데모 코드에서는 의존성이 다 추가되어있기 때문에 npm install만 해주면 된다. 테스트 코드 작성 시 테스트에서 가장 중요한 것은 자동화 된 테스트이다. `npm run watch`를 실행하여 자동화 된 테스트를 실행한다. 해당 피드백 루프를 통해 빠르게 테스트를 해볼 수 있다. 그러나 나의 노트북은 매우 느리기 때문에 코드 작성 후 한번씩 테스트를 해주기 위해 `npm test`를 사용했다.

```jsx
// App.test.jsx
describe("App", () => {
  it("renders tasks", () => {
    const { container } = render(<App />);

    expect(container).toHaveTextContent("아무 일도 하기 싫다");
  });
});
```

제일 처음에 App 컴포넌트를 대상으로 어떤 테스트 케이스를 작성할 지 작성해본다. 테스트 시 관련 테스트 코드의 그룹화를 위해 사용하는 `describe` 메소드에 테스트 대상이 되는 컴포넌트 명을 첫번째 인자로 할당한다.

그 후 두번째 인자로 어떤 테스트 케이스를 작성할 지 선언해주는데 이 때 단독 테스트 코드 작성 시 사용하는 `it` 메소드를 사용해준다.

이 때 첫번째 인자로 렌더링 테스트이므로 renders tasks라는 테스트 케이스 이름을 작성해준 뒤 Testing Library의 `render` 함수를 활용해서 `App 컴포넌트`를 먼저 그린 후 `container` 를 뽑아온 후 이 컨테이너 안에 아무 일도 하기 싫다라는 테스트 문구가 나타나도록 한다. 이 때 expect 메소드에 테스트 하는 value로 container를 전달하고 toHaveTextContent를 통해 테스트 할 텍스트를 작성해준다.

> - **container** : `render` 함수에서 리턴되는 `container`는 리액트 컴포넌트 화면에 표시되는 부분을 담고 있는 오브젝트이다.
> - **toHaveTextContent** : 엘리먼트가 특정 콘텐츠(텍스트)를 가지고 있는지 테스트하는 메소드이다.

그 후 테스트를 돌려보면 테스트가 실패하는 것을 볼 수 있다. 이유는 App 컴포넌트에 작성된 내용이 아무것도 없기 때문에 에러가 발생하는 것이다. 여기서 중요한 것은 일단 TDD 사이클에서 `실패` 단계에 돌입했다는 것이다. 다음 Step은 우선 빠르게 테스트를 통과시키는 것이다.

```jsx
// App.jsx
import React from "react";

export default function App() {
  return (
    <div>
      <h1>To-do</h1>
      <ul>
        <li>아무 일도 하기 싫다.</li>
      </ul>
    </div>
  );
}
```

위와 같이 작성하면 `App.test.jsx`의 테스트가 통과되는 것을 볼 수 있다. 하지만 이러한 모습은 우리가 원하는 모습이 아니다. 3번에서 말한 것과 같이 관심사의 분리가 필요하다. 여기서 ul 태그 부분을 분리할 수 있는데 ul 태그 부분을 List 컴포넌트로 분리할 수 있다.

```jsx
// List.jsx
const List = () => {
  return (
    <ul>
      <li>아무 일도 하기 싫다.</li>
    </ul>
  );
};

export default List;
```

우선 위와 같이 `List 컴포넌트`를 만들어 분리해준다.

```jsx
// List.test.jsx
import React from "react";

import { render } from "@testing-library/react";

import List from "./List";

describe("List", () => {
  it("renders tasks", () => {
    const { container } = render(<List />);

    expect(container).toHaveTextContent("아무 일도 하기 싫다.");
  });
});
```

우선 위와 `List.test.jsx` 테스트 파일을 생성해준 뒤 `App.test.jsx` 테스트 코드를 복사하여 기본 코드를 만들어준 후 컴포넌트를 `List 컴포넌트`로 교체해준다. 그 후 테스트해보면 테스트가 통과되는 것을 볼 수 있다.

하지만 List 컴포넌트는 위와 같은 인터페이스를 나타내지 않는다. 대부분 어떤 배열 목록을 인자로 받아서 그 배열 목록을 통해 인터페이스를 구현하고는 한다.

```jsx
<List tasks={tasks} />
```

`List.test.jsx`를 아래와 같이 수정해준다.

```jsx
// List.test.jsx
import React from "react";

import { render } from "@testing-library/react";

import List from "./List";

describe("List", () => {
  it("renders tasks", () => {
    const tasks = [{ id: 1, title: "아무 일도 하기 싫다." }];

    const { container } = render(<List tasks={tasks} />);

    expect(container).toHaveTextContent("아무 일도 하기 싫다.");
  });
});
```

그 후 `List.jsx`도 아래와 같이 수정해준다. 이 때 기존에 `App.test.jsx`에 있던 코드들의 테스트가 실패할텐데 분리된 부분을 제거해주면 된다.

```jsx
// List.jsx
import React from "react";

const List = ({ tasks }) => {
  return (
    <ul>
      {tasks?.map((task) => (
        <li key={task.id}>{task.title}</li>
      ))}
    </ul>
  );
};

export default List;
```

그 후 테스트를 통과해보면 통과되는 것을 확인할 수 있다. 하지만 이러한 테스트는 불안정하다. 리스트의 경우 여러 개의 목록이 넘어오는 것이기 때문에 여러 개의 목록을 테스트해보아야한다. 아래와 같이 리스트를 추가하여 테스트해본다.

```jsx
// List.test.jsx
import React from "react";

import { render } from "@testing-library/react";

import List from "./List";

describe("List", () => {
  it("renders tasks", () => {
    const tasks = [
      { id: 1, title: "아무 일도 하기 싫다." },
      { id: 2, title: "건물 매입" },
    ];

    const { container } = render(<List tasks={tasks} />);

    expect(container).toHaveTextContent("아무 일도 하기 싫다.");
    expect(container).toHaveTextContent("건물 매입");
  });
});
```

테스트 코드를 돌려보면 통과하는 것을 볼 수 있다. 복수의 tasks를 잘 렌더링한다는 것을 확인할 수 있다.

이제 App 컴포넌트 안에서 List 컴포넌트를 불러와 사용할 수 있게 해준다. 이 때 기존에 `App.test.jsx` 에 지웠던 코드들을 다시 살리고 App 컴포넌트 내부에서는 List 컴포넌트를 불러오고 mock list를 List 컴포넌트에 props로 넘겨준다.

```jsx
// App.jsx
import React from "react";

import List from "./List";

export default function App() {
  const tasks = [
    { id: 1, title: "아무 일도 하기 싫다." },
    { id: 2, title: "건물 매입" },
  ];

  return (
    <div>
      <h1>To-do</h1>
      <List tasks={tasks} />
    </div>
  );
}
```

```jsx
// App.test.jsx
import React from "react";

import { render } from "@testing-library/react";

import App from "./App";

describe("App", () => {
  it("renders tasks", () => {
    const { container } = render(<App />);

    expect(container).toHaveTextContent("아무 일도 하기 싫다.");
  });
});
```

위와 같이 수정하고 나면 테스트가 통과하는 것을 확인할 수 있다.

<br>

### **4-2. Redux 테스트 (09:25~)**

Redux 테스트에 앞서서 Redux를 왜 쓰는지에 대해 생각해보자. 대부분 `상태관리`라고 답변할 것이다. 하지만 Redux는 상태관리 뿐 아닌 `React의 관심사` 때문에 쓰는 것이기도 하다. 여기서 `React의 관심사`란 `State Reflection`으로 상태 반영을 말한다. State가 React 컴포넌트에 전달되면 그 컴포넌트에 전달 된 State를 바탕으로 UI를 그리기만 한다. React에 관심사는 오로지 상태 반영에만 있다. 그렇기 때문에 React는 상태 관리에는 관심이 없다.

컴포넌트 단위로 개발할 때 여러 기능들이 추가되면 컴포넌트가 비대해지는 것을 흔하게 볼 수 있다. 결과적으로 컴포넌트를 작게 유지할 수 없어서 테스트하기가 매우 번거로워 지는 상황을 볼 수 있다. 그렇기 때문에 관심사의 분리는 필수적이며 컴포넌트를 작게 유지하기 위해서 서로 상태에 대한 관심을 분리시켜야한다.

Redux 문서를 보면 `Presentational Components`와 `Container Components`를 볼 수 있다.

![Reactjs_프론트엔드에서_TDD가_가능하다는_것을_보여드립니다_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/71c6a98d-8556-4f8a-b69f-5c4ff38fd3ff)

`Container Components` 만 Redux의 존재를 알고 `Presentational Components` 는 Redux의 존재를 모른다. `Container Components` 가 Redux에서 상태를 가져오고 그 상태를 하위 컴포넌트인 `Presentational Components` 에 전달해서 UI를 그리게 되는 것이다.

그래서 중요한 것은 우리가 컴포넌트나 어떤 요소를 만들 때 항상 내가 컴포넌트라면 이게 내 관심사가 맞을까라는 질문을 던져야한다. 항상 이러한 질문들을 되풀이하며 객체 지향 원칙 중 하나인 `SRP(Single Responsibility Principle) 원칙`, 즉 단일 책임 원칙을 지키며 컴포넌트 간의 의존성을 떨어뜨려야 TDD를 원활하게 진행할 수 있는 것이다.

그러면 위에 실습에 이어 `List 컴포넌트`에 상태를 담당할 `ListContainer 컴포넌트`와 ListContainer 컴포넌트 테스트 파일을 만들어보자. 우선 `ListContainer 컴포넌트` 는 List 컴포넌트만 가질 수 있도록 한다.

```jsx
// ListContainer.jsx
import React from "react";

import List from "./List";

export default function ListContainer() {
  const tasks = [
    { id: 1, title: "아무 일도 하기 싫다." },
    { id: 2, title: "건물 매입" },
  ];

  return <List tasks={tasks} />;
}
```

그 후 테스트 파일도 작성해준다. 테스트 파일은 우선 기존 테스트 파일을 복사해서 사용한다.

```jsx
// ListContainer.test.jsx
import React from "react";

import { render } from "@testing-library/react";

import ListContainer from "./ListContainer";

describe("ListContainer", () => {
  it("renders tasks", () => {
    const { container } = render(<ListContainer />);

    expect(container).toHaveTextContent("아무 일도 하기 싫다.");
  });
});
```

위와 같이 작성이 완료되면 테스트가 통과하는 것을 볼 수 있다. 하지만 위 코드는 우리가 원하는 형식의 코드가 아니다. Redux에서 상태를 가져오는 로직으로 변경해보자.

```jsx
// ListContainer.jsx
import React from "react";

import { useSelector } from "react-redux";

import List from "./List";

export default function ListContainer() {
  const { tasks } = useSelector((state) => ({
    tasks: state.tasks,
  }));

  return <List tasks={tasks} />;
}
```

우선 ListContainer 컴포넌트 먼저 수정하였다. 이 상태에서는 테스트가 오류가 발생한다.

아직 실제로 테스트 코드 안에서는 실제 스토어를 사용할 수 없기에 에러가 발생한다. useSelector를 가짜로 구현해주어야한다. `jest`에서 제공하는 `mockImplementation`을 활용하여 함수를 조작하는데 `useSelector`는 이렇게 동작해야한다는 것을 지정해줄 수 있다.

```jsx
// ListContainer.test.jsx
import React from "react";

import { useSelector } from "react-redux";

import { render } from "@testing-library/react";

import ListContainer from "./ListContainer";

describe("ListContainer", () => {
  useSelector.mockImplementation((selector) =>
    selector({
      tasks: [
        { id: 1, title: "아무 일도 하기 싫다." },
        { id: 2, title: "건물 매입" },
      ],
    })
  );

  it("renders tasks", () => {
    const { container } = render(<ListContainer />);

    expect(container).toHaveTextContent("아무 일도 하기 싫다.");
  });
});
```

위와 같이 작성하면 테스트가 통과하지 못하는 것을 볼 수 있다. 왜냐하면 위 테스트 코드 안에서 사용 된 `useSelector`는 실제 `react-redux` 패키지에서 가져온 `useSelector` 이기 때문에 함수를 조작할 수 없기 때문이다. 그렇기 때문에 테스트 코드 내부에서 사용할 가짜 `useSelector` 를 만들어주어야 한다.

가짜 `useSelector` 를 만들기 위해서 프로젝트 최상단 경로(src와 동일 레벨)에 `jest`에서 제공하는 `__mocks__` 디렉토리를 생성한다. 그 후 이 디렉토리 내부에 파일을 생성한 뒤 mocking 할 함수들을 모아놓는다.

```jsx
// __mocks__/react-redux.js
export const useDispatch = jest.fn();

export const useSelector = jest.fn();
```

위와 같이 mock 함수인 useSelector와 useDispatch를 생성해준다. 그 후 ListContainer 테스트 파일 내부에 명시적으로 mocking 할 파일을 선택해주면 된다. (`jest.mock("파일명"`))

```jsx
// ListContainer.test.jsx
import React from "react";

import { useSelector } from "react-redux";

import { render } from "@testing-library/react";

import ListContainer from "./ListContainer";

jest.mock("react-redux"); // 추가 된 부분

describe("ListContainer", () => {
  useSelector.mockImplementaion((selector) =>
    selector({
      tasks: [
        { id: 1, title: "아무 일도 하기 싫다." },
        { id: 2, title: "건물 매입" },
      ],
    })
  );

  it("renders tasks", () => {
    const { container } = render(<ListContainer />);

    expect(container).toHaveTextContent("아무 일도 하기 싫다.");
  });
});
```

위와 같이 작성하고 나면 테스트 파일 내부 `useSelector`는 생성한 가짜 함수로 동작하게 된다. 그리고 테스트를 돌려보면 통과하는 것을 볼 수 있다.

테스트 코드를 작성하다보니 아래 코드와 같이 고정된 데이터가 중복되는 경우가 발생하는 것을 볼 수 있다. 발표를 진행하는 최수형 개발자님의 경우 이러한 데이터들은 최상위 디렉토리에 `fixtures`라는 디렉토리를 생성하여 관리한다고 하신다.

```jsx
// fixtures/tasks.js
const tasks = [
  { id: 1, title: "아무 일도 하기 싫다." },
  { id: 2, title: "건물 매입" },
];

export default tasks;
```

위와 같이 중복된 부분의 데이터를 작성한 뒤 import하여 사용해주면 깔끔하게 관리할 수 있다.

이제 `App` 컴포넌트 내부에서 사용되고 있는 `List` 컴포넌트를 `ListContainer` 컴포넌트로 바꿔주는 작업을 해야한다.

```jsx
// App.jsx
import React from "react";

import ListContainer from "./ListContainer";

export default function App() {
  return (
    <div>
      <h1>To-do</h1>
      <ListContainer />
    </div>
  );
}
```

그 후 테스트 코드를 돌려 보면 테스트가 실패한다. 이유는 App 테스트 파일 내부에서 useSelector가 mocking 되어있지 않기 때문이다. 그렇기 때문에 아래와 같이 App 컴포넌트 테스트 파일 내부에서도 useSelector mocking을 해준다.

```jsx
// App.test.jsx
import React from "react";

import { useSelector } from "react-redux";

import { render } from "@testing-library/react";

import App from "./App";

import tasks from "../fixtures/tasks";

jest.mock("react-redux");

describe("App", () => {
  useSelector.mockImplementation((selector) =>
    selector({
      tasks,
    })
  );

  it("renders tasks", () => {
    const { container } = render(<App />);

    expect(container).toHaveTextContent("아무 일도 하기 싫다.");
  });
});
```

위와 같이 수정하면 테스트가 통과하는 것을 볼 수 있다. 이로 인해 App 컴포넌트와 List 컴포넌트는 List의 상태에 대해 알지 못하고 ListContainer만이 List에 대한 상태를 알고 있게 된다. 즉 `ListContainer` 컴포넌트가 상태를 담당하는 `Container Components`, `List` 컴포넌트가 상위 컴포넌트의 상태를 받아 UI를 뿌려주는 `Presentational Components`로 관심사의 분리가 이루어지는 것을 볼 수 있다.

이제 남은 부분은 실제로 진짜 스토어에서 상태를 가져오는지를 테스트해야한다. 렌더링 초기에 데이터를 가져오기 위해 `useEffect`를 사용하고 reducer에 action을 전달하기 위해 `useDispatch`를 사용해준다. 그리고 dispatch에 전달할 `action creator`도 가져와서 action creator의 인자로 고정물인 `tasks`를 넘겨준다.

```jsx
// App.jsx
import React, { useEffect } from "react";

import { useDispatch } from "react-redux";

import ListContainer from "./ListContainer";

import { setTasks } from "./actions"; // action creator

import tasks from "../fixtures/tasks"; // fixtures

export default function App() {
  const dispatch = useDispatch();

  useEffect(() => {
    dispatch(setTasks(tasks));
  }, []);

  return (
    <div>
      <h1>To-do</h1>
      <ListContainer />
    </div>
  );
}
```

위와 같이 App 컴포넌트를 수정해준 후 src 파일 내부에 `actions.js` 파일을 생성하고 파일 내부에 `action`을 생성해준다.

```jsx
// actions.js
export function setTasks(tasks) {
  return {
    type: "setTasks",
    payload: {
      tasks,
    },
  };
}

export default {};
```

발표자 분은 action 같은 경우 복잡한 비동기 action이 아니라면 너무나 명확하기 때문에 테스트를 먼저 짜지 않고 바로 action을 생성한다고 하신다.

위와 같이 작성한 후 테스트를 돌려보면 실패하게 된다. 이유는 App 컴포넌트 내부에서 사용하는 dispatch가 정상적으로 동작하지 않기 때문이다. 그래서 이것을 통과시키기 위해서 우선 reducer를 작성해주어야한다. 우선 테스트 먼저 작성해보자. 컴포넌트 테스트가 아닌 함수 테스트 이기 때문에 확장자는 js 확장자를 활용하며 `reducer.test.js`로 파일을 생성한다.

```jsx
// reducer.test.js
import reducer from "./reducer";

import { setTasks } from "./actions";

import tasks from "../fixtures/tasks";

describe("reducer", () => {
  describe("setTask", () => {
    it("changes tasks array", () => {
      const state = reducer(
        {
          tasks: [],
        },
        setTasks(tasks)
      );

      expect(state.tasks).not.toHaveLength(0);
    });
  });
});
```

reducer를 테스트하는 것이기 때문에 우선 reducer 이름의 describe 함수를 만든다. 그 후 내부에서 setTasks에 대한 함수를 테스트하기 위해 다시 한번 setTasks 이름의 describe 함수를 만든다. 그리고 내부에서는 스토어에 있는 tasks array 상태가 변경되는 것을 확인하기 위해 it 함수를 만들어준다. 그리고 it 함수 내부에서 reducer 함수를 만들고 tasks의 초기 상태는 비어있는 array를 할당해준다. 그 후 setTasks action creator에 tasks가 전달되면 새로운 상태가 나오는데 이 부분에 대해 기대하는 부분, 즉 배열이 비어있지 않는 것을 체크하기 위해 `expect`,`not`,`toHaveLength` 함수를 활용하여 배열의 길이가 0이 아닌지를 체크한다.

테스트 작성이 완료된 후 실제 reducer도 구현해준다.

```jsx
// reducer.js
const initialState = {
  tasks: [],
};

export default function reducer(state = initialState, action) {
  if (action.type === "setTasks") {
    const { tasks } = action.payload;

    return {
      ...state,
      tasks,
    };
  }

  return state;
}
```

해당 코드 작성 후 테스트해보면 reducer 테스트 코드가 통과되는 것을 볼 수 있다. 이제 남은 것은 dispatch 작성 후 테스트가 실패하였던 App 컴포넌트의 테스트를 통과시켜야한다. App 테스트 파일을 아래와 같이 수정해준다.

```jsx
// App.test.jsx
import React from "react";

import { useDispatch, useSelector } from "react-redux";

import { render } from "@testing-library/react";

import App from "./App";

import tasks from "../fixtures/tasks";

jest.mock("react-redux");

describe("App", () => {
  const dispatch = jest.fn();

  useDispatch.mockImplementation(() => dispatch);

  useSelector.mockImplementation((selector) =>
    selector({
      tasks,
    })
  );

  it("renders tasks", () => {
    const { container } = render(<App />);

    expect(container).toHaveTextContent("아무 일도 하기 싫다.");
  });
});
```

실제 dispatch를 사용할 수 없기 때문에 `const dispatch = jest.fn()`과 같이 가짜 dispatch를 만들어준다. 그 후 이전에 만들어놓았던 가짜 `useDispatch`를 활용하여 가짜로 구현한 dispatch를 리턴하도록 한다. 이와 같이 작성하면 테스트가 통과하는 것을 볼 수 있다.

해당 테스트 코드까지 작성 후 브라우저에 앱을 띄워보면 아래와 같이 정상 동작하는 것을 확인할 수 있다.

![Reactjs_프론트엔드에서_TDD가_가능하다는_것을_보여드립니다_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/cf72c8d5-4170-4716-a3a2-4845762a51ab)

<br>

### **4-3. BDD(Behavior-driven development) (23:36~)**

이어서 진행하기 전 잠깐 BDD에 대해 알아보자. BDD(Behavior-driven development)란 행위 주도 개발로 TDD 테스트 주도 개발과 큰 차이는 없다. 테스트를 작성할 때 테스트로 생각하면 어렵기 때문에 행위 주도로, 행위 중심으로 생각해보라는 방법론이다.

예를 들어 RPG 게임이라면 검을 들고 있을때, 검을 들고 있지 않을 때, 검을 들고 있을 때는 공격이 가능하다, 검을 들고 있지 않을 때는 공격이 불가능하다 등의 테스트를 작성한다면 상황에 따라 분기가 나누어 지게 될 것이다. 이런 경우 유용하게 쓰이는게 `describe`, `context`, `it` 템플릿이다.

이것을 토대로 작성해놓은 List 컴포넌트를 더욱 고도화 시켜보자.

<br>

### **4-3. List 고도화 (24:20~)**

일단 현재 `List` 컴포넌트의 테스트에서는 `tasks`가 주어진 상황에서 `renders tasks`가 정상적으로 동작한다. 하지만 `tasks`가 주어지지 않는 경우의 케이스가 존재하지 않는다. 이러한 상황에서 할일이 없다라는 메세지를 render 하도록 상황을 나누어 코드를 작성해보자.

우선 상황을 나누어 주기 위해 `context`를 사용해야하는데 jest에서 `context`를 사용하려면 `jest-plugin-context` 패키지 의존성 설치를 해주어야한다. 의존성 설치 후 아래와 같이 작성해보자.

```jsx
// List.test.jsx
import React from "react";

import { render } from "@testing-library/react";

import List from "./List";

import tasks from "../fixtures/tasks";

describe("List", () => {
  context("with tasks", () => {
    it("renders tasks", () => {
      const { container } = render(<List tasks={tasks} />);

      expect(container).toHaveTextContent("아무 일도 하기 싫다.");
      expect(container).toHaveTextContent("건물 매입");
    });
  });
});
```

위와 같이 상황을 나누어 주기 위해 `context`로 기존 코드를 감싸준 뒤에는 테스트가 통과하는지 한번 더 체크해준다. 이와 같이 테스트 코드를 작성할 때는 수시로 테스트를 통과시켜보며 문제가 없는지 체크해주어야한다. 테스트 자동화를 켜놓고 빨간불이 뜨는지 곁눈질로 확인해주면 된다. 위 코드 작성 후 테스트가 정상적으로 통과된다면 tasks가 주어지지 않는 경우도 추가해준다.

```jsx
// List.test.jsx
import React from "react";

import { render } from "@testing-library/react";

import List from "./List";

describe("List", () => {
  context("with tasks", () => {
    const tasks = [
      { id: 1, title: "아무 일도 하기 싫다." },
      { id: 2, title: "건물 매입" },
    ];

    it("renders tasks", () => {
      const { container } = render(<List tasks={tasks} />);

      expect(container).toHaveTextContent("아무 일도 하기 싫다.");
      expect(container).toHaveTextContent("건물 매입");
    });
  });

  context("without tasks", () => {
    const tasks = [];

    it("renders no tasks message", () => {
      const { container } = render(<List tasks={tasks} />);

      expect(container).toHaveTextContent("할 일이 없어요.");
    });
  });
});
```

위에서 고정물인 tasks를 직접 작성해서 사용하는 이유는 전달하는 tasks 상태를 잘 변경하기 위해서 직접 만들어서 사용하였다. 위와 같이 테스트 코드를 작성 후 List 컴포넌트 내부도 수정해준다.

```jsx
// List.jsx
import React from "react";

const List = ({ tasks }) => {
  if (tasks.length === 0) {
    return <p>할 일이 없어요.</p>;
  }

  return (
    <ul>
      {tasks?.map((task) => (
        <li key={task.id}>{task.title}</li>
      ))}
    </ul>
  );
};

export default List;
```

위와 같이 작성이 완료된 후 테스트 코드를 돌려보면 정상적으로 통과되는 것을 확인할 수 있다.

<br>

### **4-4. 이벤트를 발생시키는 Fire Event (26:42~)**

`Fire Event`는 React Components를 테스트하는 Testing Library에서 `이벤트 발생` 테스트를 수행하는 함수이다. 진행 중인 작업에서는 추가 된 Task List 중 완료 버튼을 클릭하면 해당 Task가 제거되는 기능을 구현할 것이며 이 기능을 테스트할 때 Fire Event를 사용하려고 한다.

우선 완료 버튼을 만들어보자. 기본적으로 Task가 있을 때 완료 버튼이 있어야 하기 때문에 `List.test.jsx`에 `with tasks context` 내부에 새로운 테스트 케이스를 추가해주어야 한다.

```jsx
// List.test.jsx
import React from "react";

import { render, fireEvent } from "@testing-library/react";

import List from "./List";

describe("List", () => {
  context("with tasks", () => {
    const tasks = [
      { id: 1, title: "아무 일도 하기 싫다." },
      { id: 2, title: "건물 매입" },
    ];

    it("renders tasks", () => {
      const { container } = render(<List tasks={tasks} />);

      expect(container).toHaveTextContent("아무 일도 하기 싫다.");
      expect(container).toHaveTextContent("건물 매입");
    });

    // 추가되는 테스트 케이스
    it('renders "완료" buttons to delete a task', () => {
      const { getAllByText } = render(<List tasks={tasks} />);

      const buttons = getAllByText("완료");

      fireEvent.click(buttons[0]);
    });
  });

  context("without tasks", () => {
    const tasks = [];

    it("renders no tasks message", () => {
      const { container } = render(<List tasks={tasks} />);

      expect(container).toHaveTextContent("할 일이 없어요.");
    });
  });
});
```

우선 테스트 케이스를 추가해준 뒤 테스트 케이스를 정의해주고 내부에서는 완료 버튼에 관한 테스트를 작성해준다. 이 때 To do List에 추가되는 Task는 한 두개가 아니기 때문에 완료 버튼 또한 여러 개가 있을 수 있다. 그러므로 셀렉터는 `getAllByText` 셀렉터(셀렉터 종류는 문서를 보면 잘 나와있다.) 를 사용해준다. render 함수의 리턴 객체로부터 `getAllByText` 셀렉터를 얻어온 뒤 buttons 변수를 생성하고 셀렉터를 할당한 뒤 인자로 완료를 전달하였다. 이렇게 하면 완료라는 Text Node와 매칭되는 모든 DOM을 찾을 수 있다. 그 후 해당 버튼을 클릭하는 이벤트를 `fireEvent`를 통해 추가해주었다.

위와 같이 테스트 코드만 작성하면 당연히 테스트는 실패가 된다. 우선 테스트를 빠르게 통과시키기 위해 아래와 같이 List 컴포넌트에 완료 버튼을 추가해준다.

```jsx
// List.jsx
import React from "react";

const List = ({ tasks }) => {
  if (tasks.length === 0) {
    return <p>할 일이 없어요.</p>;
  }

  return (
    <ul>
      {tasks?.map((task) => (
        <li key={task.id}>
          {task.title}
          <button type="button">완료</button> {/* 버튼 추가 */}
        </li>
      ))}
    </ul>
  );
};

export default List;
```

위와 같이 작성하면 테스트가 통과되는 것을 확인할 수 있다.

하지만 버튼만 있는 것은 의미가 없다. 실제로 완료 버튼을 눌렀을 때 Task가 제거되는 것처럼 어떠한 상태 변화가 일어나야한다. 이 상태 변화가 일어날 때 우리가 기대할 수 있는 것은 무엇이 있을까? List 안에 있는 핸들러에서 어떤 호출이 일어나야할 것이다. 그러기 위해서 `const handleClick = jest.fn()`과 같이 가짜 함수를 생성해주고 `expect(handleClick).toBeCalled()`과 같이 호출을 체크하는 로직을 추가해준다.

또 추가로 테스트 코드 작성 시 중복 제거는 매우 중요한데 `render` 함수가 계속해서 중복으로 사용되는 것을 볼 수 있다. 이 부분도 따로 빼내어 하나로 관리할 수 있다. 아래에서는 `renderList` 함수를 생성해서 중복을 제거해주었다.

```jsx
// List.test.jsx
import React from "react";

import { render, fireEvent } from "@testing-library/react";

import List from "./List";

describe("List", () => {
  // 가짜 핸들 클릭 이벤트 생성
  const handleClick = jest.fn();

  // 중복 제거를 위해 추가
  function renderList(tasks) {
    return render(<List tasks={tasks} onClick={handleClick} />);
  }

  context("with tasks", () => {
    const tasks = [
      { id: 1, title: "아무 일도 하기 싫다." },
      { id: 2, title: "건물 매입" },
    ];

    it("renders tasks", () => {
      const { container } = renderList(tasks); // 중복 제거

      expect(container).toHaveTextContent("아무 일도 하기 싫다.");
      expect(container).toHaveTextContent("건물 매입");
    });

    it('renders "완료" buttons to delete a task', () => {
      const { getAllByText } = renderList(tasks); // 중복 제거

      const buttons = getAllByText("완료");

      fireEvent.click(buttons[0]);

      expect(handleClick).toBeCalled(); // 가짜 핸들 클릭 이벤트를 활용한 이벤트 호출 테스트
    });
  });

  context("without tasks", () => {
    const tasks = [];

    it("renders no tasks message", () => {
      const { container } = renderList(tasks); // 중복 제거

      expect(container).toHaveTextContent("할 일이 없어요.");
    });
  });
});
```

그 후 실제 List 컴포넌트에서도 props로 `onClick` 이벤트를 전달받을 수 있도록 변경해주고 완료 버튼에 해당 이벤트를 전달해준다.

```jsx
// List.jsx
import React from "react";

// onClick 추가
const List = ({ tasks, onClick }) => {
  if (tasks.length === 0) {
    return <p>할 일이 없어요.</p>;
  }

  return (
    <ul>
      {tasks?.map((task) => (
        <li key={task.id}>
          {task.title}
          <button type="button" onClick={onClick}>
            {" "}
            {/* onClick 이벤트 할당 */}
            완료
          </button>
        </li>
      ))}
    </ul>
  );
};

export default List;
```

위와 같이 작성하면 테스트는 우선 통과할 수 있다. 그 다음 실제로 상태 변화를 해주어야한다. 현재 List 상태 관리는 `ListContainer`에서 하고 있기 때문에 `ListContainer` 테스트 파일에도 테스트 케이스를 추가해준다.

```jsx
// ListContainer.test.jsx
import React from "react";

import { useDispatch, useSelector } from "react-redux";

import { render, fireEvent } from "@testing-library/react";

import ListContainer from "./ListContainer";

import tasks from "../fixtures/tasks";

jest.mock("react-redux");

describe("ListContainer", () => {
  const dispatch = jest.fn();

  useDispatch.mockImplementation(() => dispatch);

  useSelector.mockImplementation((selector) =>
    selector({
      tasks,
    })
  );

  it("renders tasks", () => {
    const { container, getAllByText } = render(<ListContainer />);

    expect(container).toHaveTextContent("아무 일도 하기 싫다.");

    const buttons = getAllByText("완료");

    fireEvent.click(buttons[0]);

    expect(dispatch).toBeCalled();
  });
});
```

위와 같이 `dispatch`를 가짜 함수로 만들고 해당 dispatch가 호출되는지 테스트하였다. 테스트 케이스 작성이 완료되었으니 실제 ListContainer 컴포넌트 내부에서도 구현을 해주어야 한다.

```jsx
// ListContainer.jsx
import React from "react";

import { useDispatch, useSelector } from "react-redux";

import List from "./List";

import { deleteTask } from "./actions";

export default function ListContainer() {
  const dispatch = useDispatch();

  const { tasks } = useSelector((state) => ({
    tasks: state.tasks,
  }));

  function handleClick(id) {
    dispatch(deleteTask(id));
  }

  return <List tasks={tasks} onClick={handleClick} />;
}
```

위와 같이 reducer에 task가 제거되는 액션(deleteTask)을 넘기기 위해 dispatch를 추가해주었다. 그 후 deleteTask 액션도 구현해준다.

```jsx
// actions.js
export function setTasks(tasks) {
  return {
    type: "setTasks",
    payload: {
      tasks,
    },
  };
}

export function deleteTask(id) {
  return {
    type: "deleteTask",
    payload: {
      id,
    },
  };
}
```

위와 같이 액션까지 작성하면 우선 테스트는 통과가 되는 것을 볼 수 있다.

그 후 reducer에서 실제로 상태를 업데이트 시키는지 테스트 하기 위한 테스트 코드를 추가해준다.

```jsx
// reducer.test.js
import reducer from "./reducer";

import { setTasks, deleteTask } from "./actions";

import tasks from "../fixtures/tasks";

describe("reducer", () => {
  describe("setTask", () => {
    it("changes tasks array", () => {
      const state = reducer(
        {
          tasks: [],
        },
        setTasks(tasks)
      );

      expect(state.tasks).not.toHaveLength(0);
    });
  });

  describe("deleteTask", () => {
    it("removes the task from tasks", () => {
      const state = reducer(
        {
          tasks: [{ id: 1, title: "아무 일도 하기 싫다." }],
        },
        deleteTask(1)
      );

      expect(state.tasks).toHaveLength(0);
    });
  });
});
```

deleteTask 테스트를 추가하여주었는데 reducer에 첫번째 인자로 mock data 중 하나를 임의로 넣어준 후 그 임의의 아이템 id를 deleteTask의 인자로 넘겨주었다. 그 후 expect를 통해 해당 reducer의 state 중 tasks를 테스트하는데 이 때 tasks로 넘겨준 아이템의 갯수가 하나이기 때문에 하나가 제거되면 해당 배열의 길이는 0이 되어야 한다. 그렇기 때문에 `toHaveLength`을 통해 해당 길이 배열이 0인지 체크해준다.

테스트 작성이 완료되었기 때문에 실제 reducer에도 구현해준다.

```jsx
const initialState = {
  tasks: [],
};

export default function reducer(state = initialState, action) {
  if (action.type === "setTasks") {
    const { tasks } = action.payload;

    return {
      ...state,
      tasks,
    };
  }

  if (action.type === "deleteTask") {
    const { tasks } = state;
    const { id } = action.payload;

    return {
      ...state,
      tasks: tasks.filter((task) => task.id !== id),
    };
  }

  return state;
}
```

deleteTask 액션 타입을 추가해주었는데 deleteTask 액션이 넘어오면 payload의 담긴 id와 현재 tasks 요소인 task의 id가 같지 않은 경우, 즉 삭제를 요청한 아이템의 id가 아닌 배열 요소들로만 필터되도록 처리한다. 이후 테스트를 해보면 정상적으로 통과되는 것을 확인할 수 있다.

이제 추가적으로 dispatch 테스트를 조금 더 구체화해보자. dispatch는 단순히 호출되는 것이 아닌 액션 타입으로 `deleteTask`가 전달되고 payload로 `id 1`을 전달하고 있다.

```jsx
// ListContainer.test.jsx
import React from "react";

import { useDispatch, useSelector } from "react-redux";

import { render, fireEvent } from "@testing-library/react";

import ListContainer from "./ListContainer";

import tasks from "../fixtures/tasks";

jest.mock("react-redux");

describe("ListContainer", () => {
  const dispatch = jest.fn();

  useDispatch.mockImplementation(() => dispatch);

  useSelector.mockImplementation((selector) =>
    selector({
      tasks,
    })
  );

  it("renders tasks", () => {
    const { container, getAllByText } = render(<ListContainer />);

    expect(container).toHaveTextContent("아무 일도 하기 싫다.");

    const buttons = getAllByText("완료");

    fireEvent.click(buttons[0]);

    expect(dispatch).toBeCalledWith({
      type: "deleteTask",
      payload: {
        id: 1,
      },
    });
  });
});
```

위와 같이 작성하면 테스트 실패가 발생한다. 어디서 문제가 발생하냐면 To Do List의 Task 완료 버튼을 클릭했을 때 id 파라미터가 넘어가야하는데 이전에 List 테스트 코드 내부 버튼 클릭 테스트에는 해당 내용이 추가되어있지 않기 때문이다. 아래와 같이 해당 내용을 적용시켜준다. 이 때 `toBeCalledWith(1)`과 같이 파라미터로 1을 넘겨주는데 위 `fireEvent.click`에서 `buttons[0]`, 즉 `첫번째 요소`를 클릭하는 것을 테스트하고 있기 때문에 id는 1을 넣어준다.

```jsx
// List.test.jsx
import React from "react";

import { render, fireEvent } from "@testing-library/react";

import List from "./List";

describe("List", () => {
  const handleClick = jest.fn();

  function renderList(tasks) {
    return render(<List tasks={tasks} onClick={handleClick} />);
  }

  context("with tasks", () => {
    const tasks = [
      { id: 1, title: "아무 일도 하기 싫다." },
      { id: 2, title: "건물 매입" },
    ];

    it("renders tasks", () => {
      const { container } = renderList(tasks);

      expect(container).toHaveTextContent("아무 일도 하기 싫다.");
      expect(container).toHaveTextContent("건물 매입");
    });

    it('renders "완료" buttons to delete a task', () => {
      const { getAllByText } = renderList(tasks);

      const buttons = getAllByText("완료");

      fireEvent.click(buttons[0]);

      expect(handleClick).toBeCalledWith(1); // 수정된 부분
    });
  });

  context("without tasks", () => {
    const tasks = [];

    it("renders no tasks message", () => {
      const { container } = renderList(tasks);

      expect(container).toHaveTextContent("할 일이 없어요.");
    });
  });
});
```

테스트 코드 수정이 완료되었으니 실제 List 컴포넌트 내부도 수정해준다. 기존 onClick을 바로 넘겨주는 형태에서 파라미터로 `task.id`를 받을 수 있게 수정해준다.

```jsx
// List.jsx
import React from "react";

const List = ({ tasks, onClick }) => {
  if (tasks.length === 0) {
    return <p>할 일이 없어요.</p>;
  }

  return (
    <ul>
      {tasks?.map((task) => (
        <li key={task.id}>
          {task.title}
          <button type="button" onClick={() => onClick(task.id)}>
            완료
          </button>
        </li>
      ))}
    </ul>
  );
};

export default List;
```

위와 같이 작성이 완료되면 테스트가 무사히 통과된다. 이제 브라우저를 띄워 기능이 정상적으로 작동하는지 테스트해본다.

![Reactjs_프론트엔드에서_TDD가_가능하다는_것을_보여드립니다_04](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/6599b011-5779-48bf-893b-5660f674d9e7)

위와 같이 정상 동작하는 것을 확인할 수 있다.

<br>

### **4-5. 비동기 액션 테스트 (37:10~)**

```jsx
// src/service/api.js
import axios from "axios";

const TASKS_URL = "https://jsonplaceholder.typicode.com/todos";

export async function fetchTasks() {
  const { data } = await axios.get(TASKS_URL);
  return data;
}

export default {};
```

axios api call을 수행하는 비동기 함수를 생성한다.

```jsx
// src/service/__mocks__/api.js
export const fetchTasks = jest.fn(async () => []);

export default {};
```

테스트 코드 내부에서 사용 할 비동기 모킹 함수를 생성한다.

```jsx
// actions.test.js
import configureStore from "redux-mock-store";

import thunk from "redux-thunk";

import { fetchTasks } from "./services/api";

import { loadTasks } from "./actions";

jest.mock("./services/api");

const middlewares = [thunk];
const mockStore = configureStore(middlewares);

describe("loadTasks", () => {
  const tasks = [
    { id: 1, title: "아무 일도 하기 싫다." },
    { id: 2, title: "건물 매입" },
  ];

  beforeEach(() => {
    fetchTasks.mockResolvedValue(tasks);
  });

  it("set tasks", async () => {
    const store = mockStore({
      tasks: [],
    });

    await store.dispatch(loadTasks());

    const actions = store.getActions();

    expect(actions).toEqual([
      { type: "setTasks", payload: { tasks: [] } },
      { type: "setTasks", payload: { tasks } },
    ]);
  });
});
```

우선 첫번째로 `mockResolvedValue`를 활용하여 가짜 비동기 함수를 구현한다. `mockResolvedValue(Promise가 resolve하는 값)` 함수를 이용하면 가짜 비동기 함수를 만들 수 있다.

```jsx
// mockResolvedValue 사용 예시
mockFn.mockResolvedValue("I will be a mock!");
mockFn().then((result) => {
  console.log(result); // I will be a mock!
});
```

그 후 해당 액션 내부에 `it` 함수에서 가짜 스토어를 구현한다. `redux-mock-store`라는 것을 이용하면 임의의 가짜 스토어를 구현할 수 있다. 가짜 스토어를 만든 뒤 해당 스토어에서 dispatch를 통해 `loadTasks`라는 비동기 액션이 일으킨다. 그 후 getActions를 통해 loadTasks라는 비동기 액션이 일어났을 때 반환하는 결과 값을 받아온다. 그 후 해당 결과 값을 테스트한다. 이 때 객체 값을 비교해야하므로 `toEqual`을 사용하였다. 이 때 배열 첫번째 요소 객체의 payload는 빈 배열이고 두번째 객체의 payload는 tasks를 받는데 이유는 `loadTasks` 비동기 액션 내부에서 확인할 수 있다. loadTasks 내부에서 dispatch를 통해 우선 빈 배열로 만든 뒤 그 후 fetchTasks를 통해 받아온 tasks로 다시 dispatch 하는 것을 볼 수 있다. 즉 두번의 걸쳐 dispatch를 하는데 toEqual 내부에서 순서대로 명시해준 것이다.

이제 실제 `loadTasks`라는 비동기 액션을 생성한다. loadTasks는 `fetchTasks`라는 비동기 axios api call을 감싸고 있다. `fetchTasks`를 이용해서 외부에서 어떤 TaskList를 받아오고 있다. 또한 dispatch를 통해 받아온 list를 스토어에 전파시키도록 한다.

```jsx
// actions.js
import { fetchTasks } from "./services/api";

export function setTasks(tasks) {
  return {
    type: "setTasks",
    payload: {
      tasks,
    },
  };
}

export function deleteTask(id) {
  return {
    type: "deleteTask",
    payload: {
      id,
    },
  };
}

export function loadTasks() {
  return async (dispatch) => {
    dispatch(setTasks([]));

    const tasks = await fetchTasks();
    dispatch(setTasks(tasks.slice(0, 10)));
  };
}
```

해당 코드까지 작성한 후 테스트 코드를 돌려보면 정상적으로 통과하는 것을 확인할 수 있다.

<br>
<br>

## **5. 정리 (38:41~)**

- TDD는 만능이 아니다. 또한 설계 방법론도 아니다. 마치 지뢰 탐지기와 같다. 지뢰 신호를 주는 지뢰 탐지기와 같고 지뢰 탐지기가 있다고 해서 모든 지뢰를 피할 수 있는 것도 아니다. 그렇기 때문에 TDD 하나만으로 좋은 설계를 나온다고 할 수는 없다. 다른 위기를 벗어나는 방법과 지식은 또 따로 학습해야한다.
- TDD를 하기 위한 필요조건은 `좋은 설계`를 해야한다. 즉 TDD를 잘하려면 좋은 설계를 해야하고 좋은 설계를 하려면 또 TDD를 잘해야 한다. 즉 뫼비우스의 띠와 같다. 결론은 둘 다 잘해야 한다.
- 이렇게 힘들고 어려운데 도대체 왜 TDD를 해야 할까? 간단하게 생각해보자. 큰 덩어리와 작은 덩어리를 비교해보았을 때 상대적으로 `작은 덩어리일 때 수정이 편하고 비용이 적게 든다.` 결국 `테스트 코드를 먼저 작성한다는 것은 전체 애플리케이션에서 작은 덩어리를 만드는 것`이다. 즉 해당 애플리케이션은 수정이 편하고 설계 개선이 쉬운 애플리케이션이 된다. 그래서 TDD가 이런 부분에서 용이하다. 즉 나중에 커진 애플리케이션에 테스트를 붙이느라 고생하는 부분, 설계 변경에서 오는 고통을 미리 당겨와서 미래의 고통을 지금으로 가져오는 기술이 TDD이다.
- TDD를 하게 되면 `요구 사항을 명확하게 하는 습관`을 갖게 된다. 팀 차원에서도 마찬가지이다. 왜냐하면 요구 사항이 명확하지 않다면 테스트를 작성할 수 없기 때문이다. TDD를 하면서 테스트 명세에 대해 자세하게 생각하게 되면서 요구 사항이 명확해지기 때문에 개발 후 `정확한 결과물을` 얻을 수 있다.
- 제일 중요한 것은 `예제로서의 스펙(Specification By Example)`이다. 테스트 코드에는 이 컴포넌트나 이 요소, 함수를 어떻게 사용할 것인가에 대한 사용 예가 다 나와있다. 그래서 개발 전 테스트 코드를 먼저 보면 사용 예를 정확하게 파악할 수 있고 문서로서 테스트도 충실히 이행할 수 있다.
- TDD를 급격하게 도입하기 보다는 기술 성속도나 비지니스 상황에 따라 유연하게 도입하는 것이 좋고 여의치 않다면 `E2E Test` 먼저 도입하는 것이 좋다. E2E Test는 사용자 관점에서 사용할 수 있는 것을 보장할 수 있기 때문이다. 발표자님의 경우 테스트를 추가하다보면 App 컴포넌트의 테스트가 비대해지는 경우가 있는데 정상 동작이 가장 중요한 것이기 때문에 App 컴포넌트의 테스트를 E2E Test로 대체한다고 하신다.
- 참고 링크

  - **실습 코드** : https://github.com/CodeSoom/frontend-tdd-feconf2020

  - **BDD** : https://www.youtube.com/watch?v=gfTsSBRvdql

  - **TDD를 해야하는 이유** : https://www.youtube.com/watch?v=j09W0KSofOk

  - **TDD 핵심** : https://www.youtube.com/watch?v=Bogx86KKp5o

  - **코딩을 하기 전에 해야 할 일** : https://www.youtube.com/watch?v=N4FV788fNiQ

<br>
