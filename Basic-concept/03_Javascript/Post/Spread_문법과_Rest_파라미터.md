# **[Javascript] Spread 문법과 Rest 파라미터**

ES6에 추가 된 Spread 문법과 Rest 파라미터 대해 알아보자. 서로 다른 문법이지만 사용법이 비슷하다.

<br>
<br>

## **1. Spread 문법**

Spread 라는 단어가 가지고 있는 의미는 확산의 의미를 가지고 있다. 이 문법을 사용하면, 객체 혹은 배열을 펼칠수 있다. 즉, Spread 문법(`...`)은 대상을 개별 요소로 분리한다. 단, Spread 문법의 대상은 이터러블이어야 한다.

<br>

### **1-1. 배열에서의 Spread 문법**

```jsx
const animals = ["개", "고양이", "참새"];
const anotherAnimals = [...animals, "비둘기"];

console.log(animals); // ['개', '고양이', '참새']
console.log(anotherAnimals); // ['개', '고양이', '참새', '비둘기']
```

<br>

### **1-2. 객체에서의 Spread 문법**

```jsx
const slime = {
  name: "슬라임",
};

const cuteSlime = {
  ...slime,
  attribute: "cute",
};

const purpleCuteSlime = {
  ...cuteSlime,
  color: "purple",
};

console.log(slime); // {name: '슬라임'}
console.log(cuteSlime); // {name: '슬라임', attribute: 'cute'}
console.log(purpleCuteSlime); // {name: '슬라임', attribute: 'cute', color: 'purple'}
```

<br>

### **1-3. 복사를 위한 Spread 문법**

```jsx
const originalArray = [1, 2, 3, 4];
const copiedArray = [...originalArray];
originalArray[0] = 100;

console.log(originalArray); // [100, 2, 3, 4]
console.log(copiedArray); // [1, 2, 3, 4]
```

배열이나 객체의 복사를 위해 사용할 수 있다. 하지만 위와 같이 1차원 참조 타입의 경우 깊은 복사처럼 동작하지만 2차원 참조 타입의 경우 얕은 복사처럼 동작한다. 이유는 `원시타입과 참조타입의 메모리 공간 할당` 포스트를 확인해보자.

<br>
<br>

## **2. Rest 파라미터**

Rest 라는 단어가 가지고 있는 의미는 나머지라는 의미를 가지고 있다. 이 문법을 사용하면, 나머지 값을 묶어서 정의할 수 있다.

<br>

### **2-1. 배열에서의 Rest 파라미터**

```jsx
// 배열에서의 Rest
const numbers = [0, 1, 2, 3, 4, 5, 6];
const [one, ...rest] = numbers;

console.log(one); // 0
console.log(rest); // [1, 2, 3, 4, 5, 6]
```

<br>

### **2-2. 객체에서의 Rest 파라미터**

```jsx
// 객체에서의 Rest
const purpleCuteSlime = {
  name: "슬라임",
  attribute: "cute",
  color: "purple",
};

const { color, ...rest } = purpleCuteSlime;
console.log(color); // purple
console.log(rest); // {name: '슬라임', attribute: 'cute'}
```

<br>

### **2-3. 함수 인자의 Rest 파라미터**

함수의 인자를 전달할 때 Rest 파라미터의 특성을 이용해서 가변 인자를 전달할 수 있다. 아래 예시 코드 내부 sum 함수는 인자로 들어오는 number를 모두 더하는 함수이다. 이 때 인자는 몇 가지가 들어올 지 모르는 가변 인자를 받고 있다. 이 때 Rest 파라미터를 사용해서 함수에 전달된 인수들의 목록을 배열로 받아 가변 인자를 받아 처리할 수 있다.

```jsx
function sum(...rest) {
  return rest.reduce((acc, current) => acc + current, 0);
}

const result = sum(1, 2, 3, 4, 5, 6);
console.log(result); // 21
```

<br>
