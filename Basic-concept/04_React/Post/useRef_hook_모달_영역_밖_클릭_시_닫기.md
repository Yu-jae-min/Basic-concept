# **# useRef hook 모달 영역 밖 클릭 시 닫기**

userMenu.current를 콘솔에 찍어보면 dom객체가 찍히는 것을 확인해볼 수 있다.

window 객체에 click 이벤트를 걸어 target이 ref에 할당한 요소에 포함되어 있는지 확인하고 조건에 따라 상태값을 변경하는 함수를 호출한다.

```javascript
const userMenu = useRef();
const [isOpen, setIsOpen] = useState(false);

const modalCloseHandler = ({ target }) => {
  if(isOpen && !userMenu.current.contains(target)) setIsOpen(false);
};

useEffect(() => {
  window.addEventListener('click', modalCloseHandler);
  return () => {
    window.removeEventListener('click', modalCloseHandler);
  };
});

return (
  {
    isOpen &&
    <Modal ref={userMenu}>
      ...
    </Modal>
  }
);
```

모달 특성상 컴포넌트가 unmount 되는 주기가 많으므로 useEffect 부수 효과 함수안의 리턴문을 통해 click 이벤트를 remove 한다.
