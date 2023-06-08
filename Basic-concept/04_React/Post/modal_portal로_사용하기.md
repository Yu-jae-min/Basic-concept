# **# modal Portals로 사용하기**

기존의 리액트에서 컴포넌트를 렌더링 하게 될 때, children 은 부모컴포넌트의 DOM 내부에 렌더링 되어야 했지만 Portals 를 사용하면 DOM 의 계층구조 시스템에 종속되지 않으면서 컴포넌트를 렌더링 할 수 있다.

modal 사용 시 다른 컴포넌트와 겹치거나 css속성인 z-index를 신경써야 한다는 문제점이 발생할 수 있다. 이러한 문제를 Portal을 통해 해결할 수 있다.

<br>

## **# 코드 구현**

### **# 1. modal이 생성 될 위치에 div 생성**

public/index.html에 root div하단에 modal_root div를 생성한다.

```html
<body>
  <noscript>You need to enable JavaScript to run this app.</noscript>
  <div id="root"></div>
  <div id="modal-root"></div>
  <!--
      This HTML file is a template.
      If you open it directly in the browser, you will see an empty page.

      You can add webfonts, meta tags, or analytics to this file.
      The build step will place the bundled scripts into the <body> tag.

      To begin the development, run `npm start` or `yarn start`.
      To create a production bundle, use `npm run build` or `yarn build`.
    -->
</body>
```

<br>

### **# 2. modal Potal 만들기**

모달 포탈을 만들어준다.

```tsx
// src/components/ModalPortal.ts
import { ReactNode } from "react";
import ReactDom from "react-dom";

interface Props {
  children: ReactNode;
}

const ModalPortal = ({ children }: Props) => {
  const el = document.getElementById("modal-root") as HTMLElement;

  return ReactDom.createPortal(children, el);
};

export default ModalPortal;
```

<br>

### **# 3. 실제 사용할 modal 만들기**

실제 사용 될 modal을 만들어준다. props로 전달받은 값은 modal 생성 후 닫기 위해 close 이벤트를 props로 전달받는다.

```tsx
// src/components/LoginModal/LoginModal.tsx
import styles from "./loginModal.module.scss";

const LoginModal = ({ onClose }: any) => {
  return (
    <div className={styles.loginModal}>
      <div className={styles.content}>
        <h3>아이디와 비밀번호 모두 입력해주세요.</h3>
        <button type="button" onClick={onClose}>
          닫기
        </button>
      </div>
    </div>
  );
};

export default LoginModal;
```

<br>

### **# 4. Portal을 사용하여 modal 사용하기**

2.에 생성해놓은 ModalPortal로 실제 사용할 modal인 LoginModal를 감싸준다.

```tsx
import { useState } from "react";
import { useNavigate } from "react-router-dom";
import { useRecoilState } from "recoil";
import { bookMarkList } from "states/atom";
import LoginModal from "components/Modal/LoginModal/LoginModal";
import ModalPortal from "components/Modal/ModalPortal";

const Login = () => {
  const [userInfo, setUserInfo] = useState({ id: "", pw: "" });
  const [userId, setUserId] = useRecoilState(bookMarkList);
  const [modalOpen, setModalOpen] = useState<boolean>();

  const navigate = useNavigate();

  const HandleUserInfo = (event: any) => {
    const { name, value } = event.currentTarget;

    const nextInput = { ...userInfo, [name]: value };
    setUserInfo(nextInput);
  };

  const HandleLoginCheck = () => {
    const { id, pw } = userInfo;
    const foamCheck = !id || !pw;

    if (foamCheck) {
      setModalOpen(true);
      return;
    }

    navigate("/");
  };

  const HandleModalShow = () => {
    setModalOpen(false);
  };

  return (
    <div className={styles.login}>
      <input type="text" name="id" onChange={HandleUserInfo} />
      <input type="password" name="pw" onChange={HandleUserInfo} />
      <button type="button" onClick={HandleLoginCheck}>
        로그인
      </button>
      {modalOpen && (
        <ModalPortal>
          <LoginModal onClose={HandleModalShow} />
        </ModalPortal>
      )}
    </div>
  );
};

export default Login;
```

위와 같이 감싸서 사용하게 되면 개발자 도구에서 아래와 같이 root div 바로 하단에 modal이 생성된 것을 확인할 수 있다.

<img width="663" alt="react_modal_Portal로_사용하기_01" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/2e4d832a-bcea-42b8-9561-f43ef4cf5a93">
