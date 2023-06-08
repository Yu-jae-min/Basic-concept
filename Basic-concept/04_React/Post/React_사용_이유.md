# # 리액트(React) 사용이유

리액트(React)는 자바스크립트 라이브러리의 하나로 SPA에 UI를 만들기 위해 사용된다.

<br>

## **# 리액트의 특징**

### **1. 가상 돔(Virtual DOM)**

가상 돔은 실제 DOM에 적용시키기 전 가상 DOM에 변화된 부분을 먼저 적용시킨 후 변화된 부분만 렌더링 되도록 하여 최소한의 연산을 통해 성능을 증가시킨다.

### **2. 단방향 데이터 바인딩**

리액트는 데이터의 흐름은 단방향이다. 즉, 위에서 아래, 부모에서 자식, 한방향으로만 흐르며 거꾸로 부모의 데이터를 바꿔주기 위해서는 state를 이용해야 한다.

### **3. JSX 문법과 선언형 프로그래밍**

JSX라는 독특한 문법 사용한다. JSX는 자바스크립트와 HTML을 동시에 사용하며, HTML에 자바스크립트의 변수들을 바로 사용할 수 있는 일종의 템플릿 언어이다. 또한 JSX문법을 활용한 선언형 프로그래밍을 사용한다.

> 프로그래밍에는 명령형 프로그래밍과 선언형 프로그래밍으로 구별할 수 있다.
>
> - 명령형 프로그래밍 : 프로그래밍을 할 때 어떻게(How)에 집중하는 것을 말한다
> - 선언형 프로그래밍 : 무엇(What)에 집중하여 프로그래밍을 하는 것을 말한다.

- 명령형 프로그래밍

```html
<ul id="”list”"></ul>
<script>
  var arr = [1, 2, 3, 4, 5];
  var elem = document.querySelector("#list");

  for (var i = 0; i < arr.length; i++) {
    var child = document.createElement("li");
    child.innerHTML = arr[i];
    elem.appendChild(child);
  }
</script>
```

- JSX를 사용한 선언형 프로그래밍

```javascript
const arr = [1, 2, 3, 4, 5];
return (
  <ul>
    {arr.map((elem) => (
      <li>{elem}</li>
    ))}
  </ul>
);
```

### **4. 컴포넌트 기반**

개별적인 뷰인 컴포넌트를 통해 UI를 구성한다.

<br>

## **# 리액트 사용 이유**

### **1. 컴포넌트화(Component)**

컴포넌트를 통해 재사용성을 증가시키고 유지보수 용이하게 함

### **2. 가상 돔(Virtual DOM)**

데이터 변경 -> 가상 DOM에 적용 -> 이전 가상 DOM과 비교 -> 변경된 부분 실제 DOM에 적용의 과정을 거쳐 DOM 연산 횟수를 줄이고 서버 부하를 줄임

### **3. 넓은 생태계**

Vue에 비해 사용자가 많고 커뮤니티나 자료가 방대

<br>

---

<br>

참고자료

- <a href="https://dev-yakuza.posstree.com/ko/react/create-react-app/react/" target='_blank'>React란</a>
