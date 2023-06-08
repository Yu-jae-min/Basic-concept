# **이벤트 전파(bubbling, capturing)**

## **# 이벤트 전파(Event propagation)**

특정 이벤트가 먼저 발생해 어떤 순서로 발생할지 정하는 것을 이벤트 전달이라고 한다.
표준 DOM 이벤트에서 정의한 이벤트 흐름엔 3가지 단계가 있다.

- 캡처링 단계 : 이벤트가 하위 요소로 전파되는 단계
- 타깃 단계 : 이벤트가 실제 타깃 요소에 전달되는 단계
- 버블링 단계 : 이벤트가 상위 요소로 전파되는 단계

공식적으론 총 3개의 이벤트 흐름이 있지만, 이벤트가 실제 타깃 요소에 전달되는 단계인 ‘타깃 단계’(두 번째 단계)는 별도로 처리되지 않는다. 캡처링과 버블링 단계의 핸들러는 타깃 단계에서 트리거된다. 즉, 버블링과 캡처링은 둘 중에 하나만 발생하는 것이 아니라 캡처링부터 시작하여 버블링으로 종료한다.

![javascript_이벤트전파_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/d986b842-c9d3-4f50-ae72-7ab3572a1844)

<br>

### **# 이벤트 버블링(Bubbling)**

이벤트 버블링(Event Bubbling)은 이벤트가 발생한 요소(하위 요소)부터 부모들(상위 요소)에게 순차적으로 이벤트가 전파되는 방식이다.

```html
<body>
  <div class="one">
    <div class="two">
      <div class="three"></div>
    </div>
  </div>
</body>
```

```javascript
var divs = document.querySelectorAll("div");

divs.forEach(function (div) {
  div.addEventListener("click", logEvent);
});

function logEvent(event) {
  console.log(event.currentTarget.className);
}

// three
// two
// one
```

위와 같은 경우 클래스 명 three를 클릭하게 되면 three -> two -> one 순서로 div 태그에 등록된 이벤트들이 실행된다. 이렇게 하위 요소에서 상위 요소로 이벤트가 전파되는 방식을 이벤트 버블링(Event Bubbling)이라고 한다.

<br>

### **# 이벤트 캡처링(Capturing)**

이벤트 캡처링(Event Capturing)은 이벤트가 발생한 요소(상위 요소)부터 자식들(하위 요소)에게 순차적으로 이벤트가 전파되는 방식이다.

```html
<body>
  <div class="one">
    <div class="two">
      <div class="three"></div>
    </div>
  </div>
</body>
```

```javascript
var divs = document.querySelectorAll("div");

divs.forEach(function (div) {
  div.addEventListener("click", logEvent, {
    capture: true, // default 값은 false
  });
});

function logEvent(event) {
  console.log(event.currentTarget.className);
}

// one
// two
// three
```

addEventListener() API에서 capture 옵션(addEventListener의 3번째 인자)의 값을 true로 설정해주면 된다. 그러면 해당 이벤트를 감지하기 위해 이벤트 버블링과 반대 방향으로 탐색한다.

위와 같은 경우 클래스 명 three를 클릭하게 되면 one -> two -> three 순서로 div 태그에 등록된 이벤트들이 실행된다. 이렇게 상위 요소에서 하위 요소로 이벤트가 전파되는 방식을 이벤트 캡처링(Event Capturing)이라고 한다.

<br>

### **# 이벤트 전파 막기**

- event.stopPropagation() : 이벤트 전파 방지, 해당 이벤트에 등록된 다른 이벤트 리스너는 실행
- event.stopImmediatePropagation() : 이벤트 전파 방지, 해당 이벤트에 등록된 다른 이벤트 리스너도 중지
- event.preventDefault() : 이벤트 취소, 태그의 기본 동작 취소

<br>

### **# target 과 currentTarget**

- event.target : 실제 이벤트가 발생하는 요소
- event.currentTarget : 이벤트 리스너가 달린 요소

<br>

### **# 이벤트 위임 (Event Delegation)**

캡쳐링과 버블링은 이벤트 위임을 위한 사전 지식이다.
실제 이벤트 위임을 통한 코딩 패턴은 자주 사용하게 되는 패턴이다.

```html
<h1>오늘의 할 일</h1>
<ul class="itemList">
  <li>
    <input type="checkbox" id="item1" />
    <label>이벤트 버블링 학습</label>
  </li>
  <li>
    <input type="checkbox" id="item2" />
    <label>이벤트 캡쳐 학습</label>
  </li>
</ul>
```

```javascript
// 수정 전 : 추가 된 아이템에 이벤트가 발생하지 않는다.
var inputs = document.querySelectorAll("input");

inputs.forEach(function (input) {
  input.addEventListener("click", function (event) {
    alert("clicked");
  });
});

// 새 리스트 아이템을 추가하는 코드
var itemList = document.querySelector(".itemList");

var li = document.createElement("li");
var input = document.createElement("input");
var label = document.createElement("label");
var labelText = document.createTextNode("이벤트 위임 학습");

input.setAttribute("type", "checkbox");
input.setAttribute("id", "item3");
label.setAttribute("for", "item3");
label.appendChild(labelText);
li.appendChild(input);
li.appendChild(label);
itemList.appendChild(li);
```

![javascript_이벤트전파_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/9bbbccdf-fb35-48b0-8767-745fbc34044d)

위 코드를 실행해보면 새로 추가 된 3번째 아이템에는 이벤트가 발생하지 않는다.
인풋 박스에 클릭 이벤트 리스너를 추가하는 시점에서 리스트 아이템은 두 개이다. 따라서, 새롭게 추가된 리스트 아이템에는 클릭 이벤트 리스너가 등록되지 않는다.

이럴 때 이벤트 위임을 사용할 수 있다.

인풋 박스의 상위 요소인 ul 태그, .itemList에 이벤트 리스너를 달아놓고 하위에서 발생한 클릭 이벤트를 감지한다. 버블링을 활용하여 이벤트 위임을 하는 것이다.

```javascript
// 수정 후
var itemList = document.querySelector(".itemList");

itemList.addEventListener("click", function (event) {
  alert("clicked");
});
```

위와 같이 패턴을 활용하면 아이템이 추가될 때마다 이벤트를 달지 않아도 된다.
아래는 주관적으로 작성해본 위 이벤트 흐름의 예시이다.

- (1) input버튼을 클릭하면 클릭 이벤트 전파가 시작된다. 캡처링->타깃->버블링 순의 흐름이다. window부터 input버튼(실제 클릭이 일어난 요소)까지 이벤트가 전파된 후 input버튼(실제 클릭이 일어난 요소)에서 window까지 역순으로 다시 전파된다.
- (2) 이 때 브라우저는 이벤트 흐름 중 클릭 이벤트 전파를 진행하며 클릭 이벤트 리스너가 심어진 객체를 찾게 된다. 위와 같은 경우 input에 상위 요소인 ul에 이벤트가 심어진 것을 확인할 수 있다.
- (3) 클릭 이벤트 리스너가 심어진 ul을 찾고 난 뒤 그 클릭 이벤트 리스너가 캡처링 단계에서 실행할 지, 버블링 단계에서 실행할 지 확인한다.
- (4) 위와 같은 경우 기본 값이기 때문에 버블링 단계에서 이벤트가 실행된다. 그렇기 때문에 window부터 실제 클릭이 일어난 input버튼까지 캡처링 단계를 지나쳐 다시 input에서 window로 전파되는 버블링 과정에서 이벤트 리스너의 콜백 함수가 실행된다. 이 때 이벤트 리스너의 콜백 함수 실행이 끝나도 이벤트 전파는 계속된다. 단, 다른 객체에는 이벤트 리스너가 걸려있지 않기 때문에 어떠한 이벤트도 실행시키지 않는 것이다.

> **input에 이벤트 리스너가 없는데 실행되는 이유! (이것도 주관적인 생각입니다.)**
>
> DOM트리가 렌더링 된 모습을 보면 레이어가 겹겹이 쌓인듯한 모습이다. 그렇기 때문에 이벤트가 일어나는 대상을 확실하게 구분하는 것이 애매하다. 만약 위와 같이 html->body->ul->li->input 경우 input을 클릭한다면 input을 클릭했는지 아니면 그 요소를 감싸고 있는 li, ul, body 등을 클릭했는지 명확하게 구분하기 어렵다. 즉 input을 감싸고 있는 모든 요소가 클릭됬다고도 할 수가 있다. 그렇기 때문에 이벤트 흐름이 발생하게 되는 것이다. 또 이벤트 흐름 중 이벤트 리스너를 만난 시점(위 기준 ul)부터 이벤트 감지를 시작하기 때문에 자식의 이벤트를 감지할 수 있는 것이다.

<br>

---

<br>

참고자료

1. <a href="https://codedragon.tistory.com/5738" target='_blank'>이벤트 전파</a>
2. <a href="https://ko.javascript.info/bubbling-and-capturing" target='_blank'>버블링과 캡처링</a>
3. <a href="https://joshua1988.github.io/web-development/javascript/event-propagation-delegation/" target='_blank'>이벤트 버블링, 이벤트 캡처 그리고 이벤트 위임까지</a>
