# **# Link tag 특정 조건에서의 페이지 이동**

프로젝트를 진행하는 도중 검색어 기능을 구현하는데 검색어 창에 입력 값이 없는 경우
페이지 이동을 막아야했다. 다시 말해 input value가 0보다 클 경우에만 Link 태그의 페이지 이동을 활성화해야했다.

<br>

## **# 코드 작성**

header에 들어가는 아이콘 메뉴 리스트였기 때문에 map함수를 활용하였다.
또한 위에서 말한 것과 같이 특정 조건에서만 페이지 이동을 해야했기 때문에 map함수 안에서 if 조건문을 활용하였다. 활용한 조건으로는 특정 조건이 false인 경우에 onClick 이벤트에 e.preventDefault()를 실행시켜 페이지 이동을 막았다. 아래 코드는 1차적으로 작성한 코드이다.

```javascript
if (inputValue.length > 0) {
  return (
    <Link className={btnClass} to="/search" key={id}>
      <img alt="cart close icon" src={url} className={iconClass} />
    </Link>
  );
} else {
  return (
    <Link
      className={btnClass}
      to="/search"
      key={id}
      onClick={(e) => e.preventDefault()}
    >
      <img alt="cart close icon" src={url} className={iconClass} />
    </Link>
  );
}
```

기능은 정상적으로 작동했지만 중복된 코드가 많고 코드의 길이가 길어 가독성이 떨어졌기 때문에 코드의 길이를 줄여줄 필요성을 느꼈다.

<br>

## **# 리팩토링**

리팩토링한 코드이다. return문 외부에 함수(testHandler)를 생성하여 함수 내부에 조건문을 작성하였다. 그 후 버튼에 onClick이벤트로 실행시켰다. 초기에 작성한 코드보다 훨씬 가독성이 좋아보인다. 아래와 같이 함수를 활용하여 조건을 걸 수도 있지만 렌더링 되는 dom요소가 적을 경우 위와 같은 방법을 써도 무관할 것 같다.

```javascript
// return문 외부
const testHandler = (event) => {
  if (inputValue.length <= 0) event.preventDefault();
};

// return문 내부
<Link className={btnClass} to="/search" key={id} onClick={testHandler}>
  <img alt="cart close icon" src={url} className={iconClass} />
</Link>;
```

<br>

---

<br>

참고자료

1. <a href="https://idenrai.tistory.com/140" target='_blank'>react-router Link Tag에서의 disabled 적용</a>
2. <a href="https://stackoverflow.com/questions/38321601/easier-way-to-to-disable-link-in-react" target='_blank'>Easier way to to disable link in React?</a>
