# [pob] POB TIL-03

## # Today I Learn - 2022.05.05

### # Pre Onboarding Course

- **팀 프로젝트** : 팀 프로젝트를 진행하였다.

1. To Do List 상세페이지 마크업 및 모달창으로 구현 - TodoList 타이틀 클릭 시 모달창이 오픈되도록 하였다. 모달의 초기 state값을 비워놓고 TodoList 클릭 시 해당 TodoList의 id와 title값을 저장하였다. state값이 존재할 경우 조건부렌더링을 활용하여 모달창을 렌더링시켰다. close와 나누어 구현한 이유는 mock data를 렌더링하는 map 메서드 내부에서 상세페이지에 사용할 id값과 title값을 받아오기 위해 open과 close를 나누어 구현하였다.

```javascript
// index.js
const handleOpenModal = (id, title) => {
  setIsOpenModal({ id, title });
};

const handleCloseModal = () => {
  setIsOpenModal("");
};
```

2. To Do List Update 기능 추가 - 상세페이지가 나타난 뒤 타이틀 부분을 클릭하여 수정할 수 있도록 하였다. 타이틀을 수정하면 그 input의 value를 state에 저장하였고 그 값을 전달받은 함수의 인자로 넘겨주었다. 함수 실행 시 item의 정보와 input value를 전달받아 클릭 된 item의 id값인 경우의 value를 수정하였다. 이 때 객체의 수정이 불가하여 원본을 깊은 복사하여 사용하였다.

```js
// index.js
const handleTodoEdit = (item, inputValue) => {
  const { id } = item;
  const elem = JSON.parse(JSON.stringify(todoList));
  const update = elem.map((el) =>
    el.id === id ? { ...el, title: inputValue } : el
  );
  setTodoList(update);

  handleCloseModal();
};

// Detail.js
const inputValueSaving = (e) => {
  setInputValue(e.target.value);
};
```

3. To Do List Delete 기능 추가 - 모달 오픈 시 사용한 state값과 삭제 함수를 상세페이지 컴포넌트로 전달하였고 상세 페이지 컴포넌트에서 휴지통 아이콘 클릭 시 전달받은 삭제 함수를 실행하며 파라미터로 state값을 전달하였다. 부모 컴포넌트에서 삭제 함수가 실행되며 클릭 된 TodoList의 id를 filter메서드로 비교하여 새로운 배열을 생성하였다. 그 후 로컬스토리지에 해당 TodoList id를 key값으로 찾아 삭제하고 모달창을 닫았다.

```js
// index.js
const handleTodoDelete = ({ id, title }) => {
  setTodoList(todoList.filter((el) => el.id !== id && el.title !== title));
  localStorage.removeItem(id);
  handleCloseModal();
};

// Delete.js
<DeleteIcon onClick={() => handleTodoDelete(item)} />;
```

<br>

## # Takeaway

오늘은 원티드 프리온보딩 코스 세번째 날이다. To do List 프로젝트를 구현하는데에 집중하였다. 이번 프로젝트에서 크게 어려움은 없었지만 작은 기능을 분담하여 작업하다보니 결국 협업하는 분과 나누어 작업하기보다는 둘 다 모든 작업을 진행하기로 하였다. 원래의 삭제 기능만 구현하는 것이 아닌 모달창으로 상세페이지를 구현하여 수정, 삭제 기능까지 구현하였다. 구현한 내용은 협업하는 분께 로컬로 공유드렸다. 작업 도중 린트에서 문제가 좀 발생하였다. 멘토님의 린트에 맞추어 작업하다보니 제약이 너무 많아지는 것 같았다. 하지만 깔끔한 코딩 습관을 위해 이런 부분들도 얼른 익숙해져야겠다. 오늘은 새롭게 배운 내용들은 많이 없었지만 개념 공부하느라, 또 인강보느라 코딩을 많이 못했었는데 그러한 부분들을 복습할 수 있었던 시간이었다.
