# 라우터(Router)

## # 라우터(Router)

<br>

### #1 SPA (Single Page Application)

싱글 페이지 애플리케이션은 서버로부터 완전한 새로운 페이지를 불러오지 않고 현재의 페이지를 동적으로 다시 작성함으로써 사용자와 소통하는 웹 애플리케이션이나 웹사이트를 말한다. 즉 페이지가 한 개인 애플리케이션을 말한다. html은 페이지 수와 같이 존재하므로 싱글 페이지 애플리켕션은 html파일이 하나가 된다.

<br>

### #2 Routing

라우팅(Routing)이란 다른 경로(url 주소)에 따라 다른 View(화면)를 보여주는 것이다. 리액트 자체에는 이러한 기능이 내장되어있지 않다. 이것이 리액트가 Framework 가 아닌 Library 로 분류되는 이유이다. 그러므로 추가적인 라이브러리를 사용하여야 하는데 이 때 사용하는 것이 React-router이다. React-router는 리액트의 라우팅 기능을 위해 가장 많이 사용 되는 라이브러리이다.

<img width="850" alt="react_라우터_01" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/b40b9f26-8094-427b-bf17-79c393db2181">

<br>

### #3 React Router

Create React App(CRA)에 특별히 routing을 위한 로직이 들어있지 않기 때문에, 가장 인기 있는 routing solution인 react-router 를 추가해서 routing을 구현한다.

<br>

#### #3-1 react-router 설치

> npm install react-router-dom --save

<br>

#### #3-2 Router 컴포넌트 구현하기

```javascript
import React from "react";
import { BrowserRouter, Routes, Route } from "react-router-dom";

import Nav from "./components/Nav/Nav";
import Footer from "./components/Footer/Footer";
import Login from "./pages/Login/Login";
import Signup from "./pages/Signup/Signup";
import Main from "./pages/Main/Main";

function Router() {
  return (
    <BrowserRouter>
      <Nav />
      <Routes>
        <Route path="/" element={<Login />} />
        <Route path="/signup" element={<Signup />} />
        <Route path="/main" element={<Main />} />
      </Routes>
      <Footer />
    </BrowserRouter>
  );
}

export default Router;
```

<br>

#### #3-3 index.js

> ReactDOM.render(<Router />, document.getElementById('root'));

현재 화면에는 App 컴포넌트가 보여지고 있다. (또는 Login 컴포넌트, Main 컴포넌트)
CRA로 만든 앱에 routing 기능을 적용하려면 index.js 를 수정해야 한다.
App 컴포넌트 대신에 routing을 설정한 컴포넌트(Router)로 변경해야 한다.

<br>

#### #3-4 Route 이동하기

Route 이동하는 방법은 두 가지가 있다.

> - Link 컴포넌트 사용하는 방법
> - useNavigate 로 구현하는 방법

#### #3-4-1 Link 컴포넌트 사용하는 방법

```javascirpt
import React from "react";
import { Link } from "react-router-dom";

function Login() {
  return (
    <div>
      <Link to="/signup">회원가입</Link>
    </div>
  );
}

export default Login;
```

Router.js 에서 설정한 path로 이동하는 첫 번째 방법은 Link 컴포넌트를 사용하는 방법이다.
react-router-dom 에서 제공하는 Link 컴포넌트는 DOM에서 a태그로 변환(Compile) 된다.

> JSX - Babel - JavaScript

a태그와 마찬가지로 Link 컴포넌트도 지정한 경로로 바로 이동시켜주는 기능을 한다.
대체로 a태그는 외부 사이트로 이동하는 경우 사용하고 Link 컴포넌트는 프로제그 내에서 페이지를 전환하는 경우 사용한다.

<br>

#### #3-4-2 useNavigate 로 구현하는 방법

```javascript
import React from "react";
import { useNavigate } from "react-router-dom";

function Login() {
  const navigate = useNavigate();

  const goToMain = () => {
    navigate("/main");
  };

  // 실제 활용 예시
  // const goToMain = () => {
  //   if(response.message === "valid user"){
  //     navigate('/main');
  //   } else {
  //     alert("가입된 회원이 아닙니다. 회원가입을 먼저 해주세요.")
  //     navigate('/signup');
  //   }
  // }

  return (
    <div>
      <button className="loginBtn" onClick={goToMain}>
        로그인
      </button>
    </div>
  );
}

export default Login;
```

Link 컴포넌트를 사용하지 않고 함수 호출을 통해 페이지를 이동하는 방법도 있다.
goToMain 함수에서 구현된 것처럼, useNavigate 훅을 통해 페이지 이동할 수 있다.
useNavigate 훅을 실행하면 페이지 이동을 할 수 있게 해주는 함수를 반환한다. 해당 함수를 navigate 라는 변수에 저장한다.
이후, navigate 의 인자로 Router.js 에서 설정한 path를 넘겨주면, 해당 경로로 이동할 수 있다.

<br>

#### #3-4-3. 두 가지 방법의 활용법

(1) Link

- 클릭 시 바로 이동하는 로직 구현 시에 사용

> Nav Bar, Aside Menu, 아이템 리스트 페이지에서 아이템 클릭 시 > 상세 페이지로 이동

(2) useNavigate

- 페이지 전환 시 추가로 처리해야 하는 로직이 있는 경우 사용

> 로그인 버튼 클릭 시
>
> - Backend API로 데이터(User Info) 전송
> - User Data 인증 / 인가
> - response message
> - Case 1 : 회원 가입되어 있는 사용자 > Main 페이지로 이동
> - Case 2 : 회원 가입이 되어 있지 않은 사용자 > Signup 페이지로 이동
