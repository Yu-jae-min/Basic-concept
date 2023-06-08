# **# 버튼 활성화 기능 구현, 배열 State 활용**

프로젝트 진행 중 여러 개의 버튼 중 하나의 버튼을 클릭했을 때, 클릭한 버튼이 활성화되면서 이전에 활성화 된 버튼이 비활성화 되는 기능 구현이 필요했다. 부모-자식 컴포넌트의 관계에서 자식 컴포넌트에 State를 생성하고 활용하면 State가 독립적으로 관리되기 때문에 그렇게 하지 않고 부모 컴포넌트에서 하나의 State를 생성한 후 관리하였다.

<br>

## #1 부모 컴포넌트에서 State와 함수 생성

```javascript
function EditSideBar() {
  const navigate = useNavigate();

  const [cateActive, setCateActive] = useState(
    Array(CREATOR_SIDEBAR_LIST.length).fill(false)
  );
  const btnActiveHandler = (id, link) => {
    const activeCheck = cateActive.map((el, index) => {
      return index === id - 1;
    });

    setCateActive(activeCheck);

    navigate(link);
  };

  return (
    <SideBarWarp>
      <CategoryWarp>
        {CREATOR_SIDEBAR_LIST.map((category) => {
          return (
            <Category
              key={category}
              cate={category}
              btnActiveHandler={btnActiveHandler}
              cateActive={cateActive}
            />
          );
        })}
      </CategoryWarp>
    </SideBarWarp>
  );
}
```

부모 컴포넌트에서 cateActive라는 배열 State를 생성하고 초기값으로 map으로 생성되는 dom의 갯수만큼 fill메소드를 통해 boolean값을 할당하였다. 이 값들 중 하나가 true로 바뀔 때 나머지 값이 false로 바뀌게 관리할 것이다. 그 후 btnActiveHandler이라는 함수를 생성하여 버튼을 클릭한 경우 클릭한 버튼의 id값과 map으로 생성되는 dom의 index를 비교하여 같은 경우만 true로 바꾸는 함수를 작성하였다. 그리고 btnActiveHandler 함수와 cateActive state를 Category라는 자식 컴포넌트로 넘겨주었다.

<br>

## #2 자식 컴포넌트에서 함수 실행, 인자 전달

```javascript
function Category({ cate, btnActiveHandler, cateActive }) {
  return (
    <div>
      <Cate
        onClick={() => btnActiveHandler(cate.id, cate.link)}
        props={cateActive}
        id={cate.id}
      >
        <NumBox props={cateActive} id={cate.id}>
          {cate.number}
        </NumBox>
        {cate.cate}
      </Cate>
    </div>
  );
}

export default Category;

const Cate = styled.button`
  display: flex;
  align-items: center;
  margin-bottom: 10px;
  padding: 12px;
  position: relative;
  width: 248px;
  height: 48px;
  border-radius: 4px;
  font-weight: 500;
  letter-spacing: -1px;
  background-color: ${({ props, id }) => (props[id - 1] ? "#f8f8f8" : "#fff")};
  color: ${({ props, id }) => (props[id - 1] ? "black" : "none")};
  font-weight: ${({ props, id }) => (props[id - 1] ? 700 : "normal")};
  &:hover {
    background-color: #f8f8f8;
  }
`;

const NumBox = styled.button`
  display: flex;
  justify-content: center;
  align-items: center;
  margin-right: 12px;
  width: 24px;
  height: 24px;
  background-color: #fff;
  border-radius: 6px;
  border: 1px solid #efefef;
  font-size: 11px;
  border: ${({ props, id }) => (props[id - 1] ? "1px solid black" : "none")};
`;
```

자식 컴포넌트에서 버튼 클릭 시 전달받은 함수를 실행하며 버튼의 id값과 이동 될 link값을 인자로 전달하였다. 여기서 전달한 id값을 map의 index와 비교하여 클릭 된 버튼만 활성화 되도록 하였다. 또한 스타일 컴포넌트에 전달받은 cateActive props로 버튼 클릭 시 스타일이 변경되도록 하였다.
