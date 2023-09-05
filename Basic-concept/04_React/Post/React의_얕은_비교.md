# [React.js] React의 얕은 비교(shallow equal)

2023년 09월 05일

<br>

# 1. React에서 얕은 비교를 수행하는 이유와 오해

기본적으로 객체를 비교할 때 얕은 비교(shallow equal)는 실제 내부 값까지 비교하는 것이 아닌 참조 주소를 비교하며 깊은 비교(deep equal)는 실제 내부 값까지 비교한다.

react에서 컴포넌트는 state 업데이트를 감지할 때 `얕은 비교`를 활용한다. state를 업데이트 할 때 spread 연산자를 통해 이전 state를 사용하고 업데이트 되는 값과 함께 사용해줌으로서 불변성(Immutability)을 유지하며 새로운 메모리 주소를 갖는 객체를 새로 생성한다. 이렇게 되면 이전 객체와 새로운 객체의 메모리 주소가 달라져 컴포넌트는 리렌더링을 발생시키게 되는 것이다.

```tsx
// spread 연산자를 활용한 불변성 유지와 업데이트
setState([...state, nextValue]);
setState({ ...state, [key]: nextValue });
```

만약 위와 같이 state가 객체나 배열처럼 참조 타입인 경우 내부 값을 직접 변경하게 되면 참조 주소가 변경되지 않기 때문에 컴포넌트가 state의 업데이트를 감지할 수 없게 되어 리렌더링이 발생하지 않는다.

위 내용이 기본적으로 알고 있었던 내용이었다.

그런데 어떤 react 렌더링 관련 포스트를 읽으며 react의 얕은 비교는 “**두 개의 서로 다른 객체의 모든 개별 필드를 확인하고 객체의 내용이 서로 다른 값인지 확인하는 것을 의미한다**.”라는 말을 보았다. 또한 공식 문서에도 아래와 같이 나와있다. (https://legacy.reactjs.org/docs/shallow-compare.html#overview)

> shallowCompare performs a shallow equality check on the current props and nextProps objects as well as the current state and nextState objects.
> It does this by iterating on the keys of the objects being compared and returning true when the values of a key in each object are not strictly equal.
>
> shallowCompare는 현재의 props와 nextProps 객체, 그리고 현재의 state와 nextState 객체에 대해 얕은 동등성 검사를 수행합니다. 이 작업은 비교 대상 객체의 키를 반복하면서 각 객체의 해당 키의 값이 엄격하게 동일하지 않을 때 true를 반환하여 수행됩니다.

위 내용을 요약해보면 얕은 비교는 객체의 업데이트를 확인할 때 두 객체의 모든 key의 value가 동일하지 않을 때 true를 반환하여 업데이트 된다고 한다. 즉 모든 key의 검사를 수행하는 것이다.

얕은 비교는 참조 주소만 비교하는 것으로 알고 있었는데 이게 무엇을 의미하는 것일까?

<br>
<br>

# 2. React의 얕은 비교 알아보기

우선 동작 방식을 확인하기 위해 react에서 얕은 비교를 수행할 때 사용되는 코드를 살펴보자. (https://github.com/facebook/react/blob/main/packages/shared/shallowEqual.js)

```tsx
// react/packages/shared/shallowEqual.js
function shallowEqual(objA, objB) {
  // 1. 값 체크 : 두 값이 같은 지 확인 (참조 타입의 경우 동일 참조인지 확인, 원시 타입인 경우 값 체크)
  if (is(objA, objB)) {
    return true;
  }

  // 2. type과 null 체크 : 두 값이 참조 타입이 아니거나 null이라면 false
  if (
    typeof objA !== "object" ||
    objA === null ||
    typeof objB !== "object" ||
    objB === null
  ) {
    return false;
  }

  // 3. key 배열 생성 : 비교하는 두 객체의 key를 배열로 변환한다.
  const keysA = Object.keys(objA);
  const keysB = Object.keys(objB);

  // 4. key 길이 비교 : key의 길이를 체크하여 변경되었으면 false를 반환한다.
  if (keysA.length !== keysB.length) {
    return false;
  }

  // 5. A의 키가 B와 다른지 테스트한다. 이전 값인 keysA의 key 배열을 기준으로 반복한다.
  for (let i = 0; i < keysA.length; i++) {
    const currentKey = keysA[i];

    // 조건 1, key 변경 확인 : 이전 객체 keysA의 key가 업데이트 객체 objB에 존재하지 않으면 false를 반환한다.
    // 조건 2, value 업데이트 확인 : 이전 객체 내부 현재 key의 value와 업데이트 객체 내부 현재 key의 value가 같지 않으면 false를 반환한다.
    if (
      !hasOwnProperty.call(objB, currentKey) ||
      !is(objA[currentKey], objB[currentKey])
    ) {
      return false;
    }
  }

  // 6. 동일 값 판별 : 위의 조건들이 모두 걸리지 않는다면 동일한 값으로 판별한다.
  return true;
}
```

주석은 간단한 해석을 달아 놓았다. 위 코드를 보면 1번에서 is 함수를 통해 객체 자체를 비교하고 5번의 for문 안에서 두 객체 프로퍼티의 value를 비교하고 있는 것 같다.

더 자세히 알아보기 위해 is 함수의 폴리필 코드를 확인해보자.

```tsx
// react/packages/shared/objectIs.js
function is(x: any, y: any) {
  return (x === y && (x !== 0 || 1 / x === 1 / y)) || (x !== x && y !== y);
}

const objectIs: (x: any, y: any) => boolean =
  typeof Object.is === "function" ? Object.is : is;

export default objectIs;
```

위 코드는 `is` 폴리필 코드이다. 코드를 해석해보면 첫번째 조건의 경우 x와 y가 같고 x가 0이 아니거나 1을 x로 나눈 값과 y로 나눈 값이 같은 경우이고 두번째 조건의 경우 x가 x와 다르고 y가 y와 다른 경우, 즉 NaN인 경우를 나타낸다.

해당 코드를 테스트해보자. 우선 다른 메모리 주소를 가지는 objA와 objB를 is 함수의 인자로 넘겨주었다. 결과는 아래와 같다.

```tsx
function is(x, y) {
  console.log("x === y", x === y); // false
  console.log("x !== 0", x !== 0); // true
  console.log("1 / x", 1 / x); // NaN
  console.log("1 / y", 1 / y); // NaN
  console.log("1 / x === 1 / y", 1 / x === 1 / y); // false
  console.log("x !== x", x !== x); // false
  console.log("y !== y", y !== y); // false

  return (x === y && (x !== 0 || 1 / x === 1 / y)) || (x !== x && y !== y);
}

const objA = { a: "1" };
const objB = { a: "2" };

is(objA, objB); // false
```

첫번째 조건 중 타입까지 비교하는 `===` 엄격한 비교의 경우 객체의 메모리 주소가 다르기 때문에 false를 반환하는 것을 볼 수 있다. 그러면 객체의 메모리 주소가 동일한 값을 전달해보자.

```tsx
function is(x, y) {
  console.log("x === y", x === y); // true
  console.log("x !== 0", x !== 0); // true
  console.log("1 / x", 1 / x); // NaN
  console.log("1 / y", 1 / y); // NaN
  console.log("1 / x === 1 / y", 1 / x === 1 / y); // false
  console.log("x !== x", x !== x); // false
  console.log("y !== y", y !== y); // false

  return (x === y && (x !== 0 || 1 / x === 1 / y)) || (x !== x && y !== y);
}

const objA = { a: "1" };
const objB = { a: "2" };

is(objA, objA); // true
```

위 코드를 보면 is 함수의 인자로 objA를 두 번 넘겨주고 있다. 즉 같은 참조를 가리키는 객체를 넘겨준 것인데 이 때 결과를 확인해보면 true를 반환하는 것을 알 수 있다.

이제 is 함수의 동작 방식을 알았으니 `shallowEqual` 함수를 테스트해보자.

```tsx
const objA = { a: "1" };
const objB = { a: "1" };
const objC = { b: "1" };
const objD = { a: "1", b: "1" };

console.log(shallowEqual(objA, objA)); // true
console.log(shallowEqual(objA, objB)); // true
console.log(shallowEqual(objA, objC)); // false
console.log(shallowEqual(objA, objD)); // false
```

위 결과를 확인해보면 다음과 같다.

1. **참조가 같은 경우** : true를 반환한다. 참조가 같기 때문에 `shallowEqual` 함수 내부 1번에 `is(objA, objB)` 조건에서 true를 반환하게 된다.

2. **참조는 다르지만 프로퍼티가 같은 경우** : true를 반환한다. `shallowEqual` 함수 내부 어떠한 조건에도 걸리지 않기 때문에 최종 출력 값인 true를 반환한다.

3. **참조와 프로퍼티가 모두 다른 경우** : false를 반환한다. 비교 대상 객체 내부에 기존 프로퍼티 key가 존재하지 않기 때문에 `shallowEqual` 함수 내부에서 키의 존재 유무와 키의 value를 비교하는 5번 반복문 내부 조건 1과 2에 모두 걸리게 된다.

4. **참조가 다르고 프로퍼티가 포함되어 있는 경우** : false를 반환한다. 비교 대상 객체의 프로퍼티의 개수와 기존 프로퍼티 개수가 다르기 때문에 `shallowEqual` 함수 내부에서 프로퍼티 키 배열의 길이를 비교하는 4번에 걸리게 된다.

<br>
<br>

# 3. 정리하기

### 3-1. 얕은 비교를 수행하는 `shallowEqual` 함수의 역할

1. is 폴리필 함수 내부에서 파라미터로 전달 받은 두 값이 참조 타입인 경우 참조가 같은 지, 원시 타입인 경우 값이 같은지, undefined이거나 NaN이 아닌지 등을 체크

2. 참조 타입이 아니거나 null인 경우를 체크

3. 참조 타입인 경우 기존 객체의 key 개수와 비교 객체의 key 개수 비교

4. 참조 타입인 경우 기존 객체의 key가 비교 객체의 key로 존재하는지 여부 체크 및 비교 객체와 value 비교

<br>

## 3-2. 결론

1. react의 얕은 비교는 대상을 참조(주소값)로만 비교하지 않는다.

2. 참조 타입을 비교하는 경우 참조가 같을 때는 같은 값으로 취급하고 참조가 다를 때에는 property key와 value 전체에 대해 검사를 진행하여 모두 같은 경우 같은 값으로 취급한다.

3. 원시 타입을 비교하는 경우 값을 비교한다. (undefined이거나 NaN이 아닌지 등 체크)

4. 깊은 비교와 차이는 객체를 만날 경우 재귀적으로 마지막 depth까지 비교를 진행한다.

<br>
<br>

# 0. 참고 URL

- [https://velog.io/@jinhyukoo/React-얕은-비교에-대한-얕은-오해#reference](https://velog.io/@jinhyukoo/React-%EC%96%95%EC%9D%80-%EB%B9%84%EA%B5%90%EC%97%90-%EB%8C%80%ED%95%9C-%EC%96%95%EC%9D%80-%EC%98%A4%ED%95%B4#reference)
- [https://velog.io/@superlipbalm/blogged-answers-a-mostly-complete-guide-to-react-rendering-behavior#컴포넌트-렌더링-최적화-기법](https://velog.io/@superlipbalm/blogged-answers-a-mostly-complete-guide-to-react-rendering-behavior#%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8-%EB%A0%8C%EB%8D%94%EB%A7%81-%EC%B5%9C%EC%A0%81%ED%99%94-%EA%B8%B0%EB%B2%95)
- https://legacy.reactjs.org/docs/shallow-compare.html#overview
- https://github.com/facebook/react/blob/main/packages/shared/shallowEqual.js
- https://github.com/facebook/react/blob/main/packages/shared/objectIs.js
- https://github.com/facebook/react/blob/main/packages/shared/hasOwnProperty.js
- https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/is

<br>
