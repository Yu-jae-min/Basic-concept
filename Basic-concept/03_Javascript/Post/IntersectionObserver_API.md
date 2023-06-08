# **IntersectionObserver API**

## **# IntersectionObserver API**

IntersectionObserver는 WebAPI로 비동기적으로 실행되며 관찰 대상과 뷰포트의 교차점을 관찰하고 뷰포트 안으로 들어오는 시점에 정보를 제공하는 기능을 한다.
아래와 같은 상황에 활용한다.

- 페이지가 스크롤되는 도중에 발생하는 이미지나 다른 콘텐츠의 지연 로딩
- 무한 스크롤(infinite-scroll) 구현
- 광고 수익을 계산하기 위한 용도로 광고의 가시성 보고
- 사용자에게 결과가 표시되는 여부에 따라 작업이나 애니메이션 수행 여부

<br>

## **# Intersection Observer API 사용법**

### **# 1. Intersection observer 생성**

Intersection observer를 생성하기 위해서는 생성자 호출 시 콜백 함수를 제공해야 한다. 이 콜백은 함수 threshold가 한 반향 혹은 다른 방향으로 교차할 때 실행된다.

```js
let options = {
  root: document.querySelector("#scrollArea"),
  rootMargin: "0px",
  threshold: 1.0,
};

let observer = new IntersectionObserver(callback, options);
```

<br>

### **# 2. Intersection observer 설정**

- **root** : 대상 객체의 가시성을 확인할 때 사용되는 뷰포트 요소이며 root는 대상 객체의 조상 요소여야 한다. default는 브라우저의 viewport이다.
- **rootMargin** : root가 가진 여백으로 이 속성의 값은 css의 margin 속성과 비슷하며 rootMargin은 root 요소의 각 측면의 bounding box를 수축시키거나 증가시키며, 교차성을 계산하기 전에 적용된다. default는 0이다.
- **threshold** : observer의 콜백이 실행될 대상 요소의 가시성 퍼센티지를 나타내는 단일 숫자 혹은 배열이다. 만약 50%만큼 요소가 보였을 때를 탐지하고 싶다면, 값을 0.5로 설정하면 된다. 또는 25% 단위로 요소의 가시성이 변경될 때마다 콜백이 실행되게 하고 싶다면 [0, 0.25, 0.5, 0.75, 1]과 같이 배열을 설정하면 된다. default는 0이며 이는 요소가 1px이라도 보이자마자 콜백이 실행됨을 의미한다. 1.0은 요소의 모든 픽셀이 화면에 노출되기 전에 콜백을 실행시키지 않음을 의미한다.

<br>

### **# 3. Intersection Observer Callback 형태**

```js
let callback = (entries, observer) => {
  entries.forEach((entry) => {
    // Each entry describes an intersection change for one observed
    // target element:
    //   entry.boundingClientRect
    //   entry.intersectionRatio
    //   entry.intersectionRect
    //   entry.isIntersecting
    //   entry.rootBounds
    //   entry.target
    //   entry.time
  });
};
```

<br>

### **# 4. Intersection observer을 통해 타깃으로 하는 요소 관찰하기**

```js
let target = document.querySelector("#listItem");

observer.observe(target);
```

<br>

## **# Intersection Observer API 실제 활용**

### **# 동적 이미지 로딩**

IntersectionObserver를 이용하면 동적 이미지 로딩을 손쉽게 구현 할 수 있다. 구현 방법은 대상 element가 뷰포트에 들어왔을 때 이미지 경로를 변경 한 뒤 unobserve시킨다. 다음의 코드는 간단한 예제 코드이다.

```html
<div class="example">
  <img
    src="https://picsum.photos/600/400/?random?0"
    alt="random image"
    class="image-default"
  />
  <img
    data-src="https://picsum.photos/600/400/?random?1"
    alt="random image"
    class="image"
  />
  <img
    data-src="https://picsum.photos/600/400/?random?2"
    alt="random image"
    class="image"
  />
  <img
    data-src="https://picsum.photos/600/400/?random?3"
    alt="random image"
    class="image"
  />
  <img
    data-src="https://picsum.photos/600/400/?random?4"
    alt="random image"
    class="image"
  />
  <img
    data-src="https://picsum.photos/600/400/?random?5"
    alt="random image"
    class="image"
  />
  <img
    data-src="https://picsum.photos/600/400/?random?6"
    alt="random image"
    class="image"
  />
  <img
    data-src="https://picsum.photos/600/400/?random?7"
    alt="random image"
    class="image"
  />
</div>
```

동적 이미지 로딩을 수행할 이미지 태그의 경우 dataset 속성에 이미지 url을 담아둔다.
그 후 IntersectionObserver API를 활용하여 관찰하는 뷰포트 안으로 들어왔을 경우 dataset 속성에 이미지 url을 src 속성으로 할당해준다. 주의해야 할 점은 사용자에게 바로 노출되는 최상위 이미지의 경우 동적 이미지 로딩이 필요하지 않으므로 일반적인 방법과 같이 src 속성에 이미지 url을 담아둔다.

```js
// IntersectionObserver의 options를 설정
const options = {
  root: null,
  // 타겟 이미지 접근 전 이미지를 불러오기 위해 rootMargin을 설정
  rootMargin: "0px 0px 30px 0px",
  threshold: 0,
};

// IntersectionObserver 를 등록
const io = new IntersectionObserver((entries, observer) => {
  entries.forEach((entry) => {
    // 관찰 대상이 viewport 안에 들어온 경우 image 로드
    if (entry.isIntersecting) {
      // data-src 정보를 타켓의 src 속성에 설정
      entry.target.src = entry.target.dataset.src;
      // 이미지를 불러왔다면 타켓 엘리먼트에 대한 관찰 멈춤
      observer.unobserve(entry.target);
    }
  });
}, options);

// 관찰할 대상을 선언하고, 해당 속성을 관찰
const images = document.querySelectorAll(".image");
images.forEach((el) => {
  io.observe(el);
});
```

<br>

### **# 무한 스크롤**

무한 스크롤 기능도 IntersectionObserver를 이용하면 쉽게 구현 할 수 있다.

```html
<div class="container">
  <div id="items"></div>
  <div id="loader"></div>
</div>
```

컨테이너 역할을 하는 DOM의 하단에 추가 로딩을 위한 element를 추가 한뒤, 해당 element가 뷰포트에 접근했을 때 추가 컴포넌트 또는 이미지를 로딩 하면 된다. 이미지 동적 로딩 때와는 달리, 계속해서 추가 로딩을 해야하기 때문에 unobserve는 하지 않는다.

```js
const count = 20;
let index = 0;

const loadItems = () => {
  const fragment = document.createDocumentFragment();

  for (let i = index; i < index + count; i += 1) {
    const item = document.createElement("div");
    item.innerText = `${i + 1}`;
    item.classList.add("item");
    fragment.appendChild(item);
  }

  document.getElementById("items").appendChild(fragment);
  index += count;
};

const observer = new IntersectionObserver(([loader]) => {
  if (!loader.isIntersecting) return;

  loadItems();
});

loadItems();
observer.observe(document.getElementById("loader"));
```

<br>

---

<br>

참고자료

- <a href="https://armadillo-dev.github.io/javascript/what-is-intersection-observer/" target='_blank'>[Javascript] IntersectionObserver API 설명과 사용 방법</a>
- <a href="https://woojong92.tistory.com/entry/JS-Intersection-Observer-API-%EC%82%AC%EC%9A%A9%EB%B2%95%EA%B3%BC-%ED%99%9C%EC%9A%A9" target='_blank'>[JS] Intersection Observer API 사용법과 활용</a>
