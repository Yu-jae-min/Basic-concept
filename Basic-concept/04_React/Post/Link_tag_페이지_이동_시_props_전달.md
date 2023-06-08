# **# Link tag 페이지 이동 시 props 전달하기**

프로젝트 진행 중 검색 기능을 구현하는데 검색어 입력 후 페이지를 이동하는데 페이지 이동 시 해당 검색어 데이터를 이동 된 페이지에 넘겨주어야했다.

<br>

## **# to attribute안에 작성(?)**

평소와 마찬가지로 구글링을 시작했다. 그러다보니 아래와 같은 공통된 코드 형태를 찾아볼 수 있었다. Link 태그에 경로를 지정하는 to 속성안에 pathname, search, hash, state 등의 값을 함께 입력하는 형태이며 state는 객체 형태로 전달한다.

```javascript
<Link to={
  {
    pathname: '/search',
    state: {
      data1: year,
      data2: title,
      data3: summary
    }
  }
}>
```

<br>

## **# useLocation hook**

위와 같이 코드를 작성한 후 state가 정확히 전달되었는지 확인하기 위해 useLocation hook을 사용하였다. useLocation hook은 사용자가 현재 머물러있는 페이지에 대한 정보를 알려주는 hook 이고, defaultProps 하나인 location 객체를 대체 하는 react-router-dom hooks이다.

```javascript
import React from "react";
import { useLocation } from "react-router";

const Search = () => {
  const location = useLocation();
  console.log(location);

  return (
    <div>
      <span>Hello World!</span>
    </div>
  );
};
```

위와 같이 useLocation hook을 이용하여 콘솔에 state값을 찍어보았다. 하지만 state값이 찍히지 않았다. pathname, search, hash와 같은 다른 값들은 정상적으로 들어오는데 유독 state값만 계속해서 null이 찍혔다. 분명 페이지 이동 전 Link 버튼의 상태를 react extention으로 체크했을 때는 state가 정상적으로 담겨져있었지만 Link 버튼으로 페이지 이동 후에는 데이터가 전달되지 않았다.

<br>

## **# state null 해결 방안**

아래와 같이 해결하였다. to 속성안에 함께 작성하는 것이 아닌 to 속성과 같은 레벨에서 state속성을 작성하니 해결되었다. 별거 아니지만 많이 헤맸다. 위와 같은 방법이 왜 적용되지 않았는지는 더 찾아보며 추가적인 포스팅을 작성해야겠다.

```javascript
<Link
	to={{
    pathname: '/search'
    state: {
      data1: year,
      data2: title,
      data3: summary
    }
  }}
/>
```

<br>

## **# enter 이벤트 처리 (2022.02.07 추가)**

Link 태그를 이용하여 페이지 이동 시 props 넘겨주는 작업을 하였다. 하지만 Link 태그 클릭 시에는 props가 제대로 전달됬는데 추가로 enter 이벤트 처리를 해야했기 때문에 한번 더 리팩토링이 진행되었다. 단순 페이지 내부 이동을 넘어 추가적인 처리가 필요했기 때문에 Link 태그 대신 useNavigate를 활용하였다. useNavigate도 Link 태그와 마찬가지로 props를 담아 전달하는 것이 가능했다. 그렇기 때문에 함수를 따로 생성하여 조건문을 작성하고 그 후 페이지 이동과 함께 props가 전달되도록 작성하였다.

```javascript
// return문 외부
const navigate = useNavigate();

const handleClick = (event) => {
  if (event.key === "Enter") {
    navigate("/Search", {
      state: {
        data1: year,
        data2: title,
        data3: summary,
      },
    });
  }
};

// return 내부
<input
  className="searchInput"
  placeholder="검색어를 입력해주세요."
  onKeyPress={handleClick}
/>;
```

그 후 이동 된 페이지에서 상단에 작성된 방법대로 useLocation hook을 이용하여 전달받은 props를 사용하였다.

```javascript
const location = useLocation();
console.log(location.state.inputValue);
```

<br>

---

<br>

참고자료

1. <a href="https://velog.io/@yiyb0603/React-Router-dom%EC%9D%98-%EC%9C%A0%EC%9A%A9%ED%95%9C-hooks%EB%93%A4" target='_blank'>React Router dom의 유용한 hooks들</a>
2. <a href="https://stackoverflow.com/questions/67061088/can-not-pass-state-with-react-router-dom-v6-beta-state-is-null" target='_blank'>Can not pass state with react router dom v6 beta, state is null</a>
3. <a href="https://ui.dev/react-router-pass-props-to-link/" target='_blank'>How to Pass Props Through React Router's Link Component</a>
