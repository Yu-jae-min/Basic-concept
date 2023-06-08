# **# 얕은 복사(Shallow Copy)와 깊은 복사(Deep Copy)**

얕은 복사는 객체의 참조값(주소 값)을 복사하고, 깊은 복사는 객체의 실제 값을 복사한다.
자바스크립트에서 값은 원시값과 참조값 두 가지 데이터 타입의 값이 존재한다.
자바스크립트에서 원시 타입(primitive type)의 값은 새로운 메모리 공간에 독립적인 값을 저장하기 때문에 깊은 복사가 되고 참조 타입(reference type)값은 얕은 복사가 된다. 원시 타입과 참조 타입의 가장 큰 차이점은 원본이 바뀌면 참조 타입은 복사본도 같이 변경되지만, 원시 타입은 변경되지 않는다는 점이 큰 차이점이다.

```javascript
// 원시 타입의 깊은 복사
let a = "원본 데이터";
let b = a;

a = "수정 데이터";

console.log(a); // '수정 데이터'
console.log(b); // '원본 데이터'
```

원시 타입은 복사 시 값 자체를 담은 독립적인 메모리를 생성하기 때문에 a가 재할당 되더라도 b에는 아무런 영향을 미치지 않는다.

<br>

```javascript
// 참조 타입의 얕은 복사
let a = { name: "원본 데이터" };
let b = a;

a.name = "수정 데이터";

console.log(a); // '수정 데이터'
console.log(b); // '수정 데이터'
```

원시 타입과 달리 참조 타입인 오브젝트는 새로운 값으로 변수 값을 재할당 하자 복사된 변숫값도 같이 변경되는 것을 확인할 수 있다. 즉, 데이터가 그대로 하나 더 생성된 것이 아닌 해당 데이터의 메모리 주소를 전달하게 돼서, 결국 한 데이터를 공유하게 되는 걸 알 수 있다.

<br>

### **#1 얕은 복사(Shallow Copy)**

얕은 복사란 객체를 복사할 때 기존 값과 복사된 값이 같은 참조를 가리키고 있는 것을 말한다. 객체 안에 객체가 있을 경우 한 개의 객체라도 기존 변수의 객체를 참조하고 있다면 이를 얕은 복사라고 한다.

- 객체를 복사할 때, 해당 객체만 복사하여 새 객체를 생성한다.
- 복사된 객체의 인스턴스 변수는 원본 객체의 인스턴스 변수와 같은 메모리 주소를 참조한다.
- 따라서, 해당 메모리 주소의 값이 변경되면 원본 객체 및 복사 객체의 인스턴스 변수 값은 같이 변경된다.

<br>

#### **Array.prototype.slice()**

얕은 복사 방법의 대표적인 예라고 할 수 있다. start부터 end 인덱스까지 기존 배열에서 추출하여 새로운 배열을 리턴하는 메소드이다. 만약 start와 end를 설정하지 않는다면, 기존 배열을 전체 얕은 복사한다.

```javascript
const original = ["a", 2, true, 4, "hi"];
const copy = original.slice();

console.log(JSON.stringify(original) === JSON.stringify(copy)); // true

copy.push(10);

console.log(JSON.stringify(original) === JSON.stringify(copy)); // false

console.log(original); // [ 'a', 2, true, 4, 'hi' ]
console.log(copy); // [ 'a', 2, true, 4, 'hi', 10 ]
```

기존 배열에는 영향을 끼치지 않아서 깊은 복사로 보일 수 있지만, 원시값을 저장한 1차원 배열일 뿐이다. 원시값은 기본적으로 깊은 복사이다. Slice() 메소드는 기본적으로 얕은 복사를 수행한다.

```javascript
const original = [
  [1, 1, 1, 1],
  [0, 0, 0, 0],
  [2, 2, 2, 2],
  [3, 3, 3, 3],
];

const copy = original.slice();

console.log(JSON.stringify(original) === JSON.stringify(copy)); // true

// 복사된 배열에만 변경과 추가.
copy[0][0] = 99;
copy[2].push(98);

console.log(JSON.stringify(original) === JSON.stringify(copy)); // true

console.log(original);
// [ [ 99, 1, 1, 1 ], [ 0, 0, 0, 0 ], [ 2, 2, 2, 2, 98 ], [ 3, 3, 3, 3 ] ]출력
console.log(copy);
// [ [ 99, 1, 1, 1 ], [ 0, 0, 0, 0 ], [ 2, 2, 2, 2, 98 ], [ 3, 3, 3, 3 ] ]출력
```

만약 1차원 배열이 아닌 중첩 구조를 갖는 2차원 배열이면 얕은 복사를 수행하게 된다.

```javascript
const original = [
  {
    a: 1,
    b: 2,
  },
  true,
];
const copy = original.slice();

console.log(JSON.stringify(original) === JSON.stringify(copy)); // true

// 복사된 배열에만 변경.
copy[0].a = 99;
copy[1] = false;

console.log(JSON.stringify(original) === JSON.stringify(copy)); // false

console.log(original);
// [ { a: 99, b: 2 }, true ]
console.log(copy);
// [ { a: 99, b: 2 }, false ]
```

또 다른 예시이다. 배열 안에 객체를 수정하고자 할 경우 얕은 복사를 수행하는 것을 볼 수 있다. 하지만 원시값은 기본적으로 깊은 복사라 기존 변수에 있는 값과는 다른 값을 도출하는 것을 볼 수 있다.

<br>

#### **Object.assign()**

Object.assign(생성할 객체, 복사할 객체)
메소드의 첫 번째 인자로 빈 객체를 넣어주고 두 번째 인자로 복사할 객체를 넣어준다.
이 때 메소드 첫번째 인자로 객체를 넣어주게 되면 그 객체에 추가로 더해진 객체가 생성된다.

```javascript
const obj = { a: 1 };
const newObj = Object.assign({}, obj);

newObj.a = 2;

console.log(obj); // { a: 1 }
console.log(obj === newObj); // false
```

새로운 newObj 객체를 Object.assign() 메소드를 사용하여 생성하였으며, newObj.a 값을 변경하여도 기존의 obj는 변하지 않았다. 서로의 객체를 비교해도 false로 뜨며 서로 참조값이 다르다는 것을 알 수 있다.

하지만 Object.assign()를 활용한 복사는 완벽한 깊은 복사가 아니다.
Object.assign()는 2차원 객체는 깊은 복사가이루어지지 않는다

MDN에서는 "Object.assign()은 속성의 값을 복사하기때문에 다른 대안을 사용해야합니다. 출처 값이 객체에 대한 참조인 경우, 참조 값만을 복사합니다."라고 설명한다.

```javascript
const obj = {
  a: 1,
  b: {
    c: 2,
  },
};

const newObj = Object.assign({}, obj);

newObj.b.c = 3;

console.log(obj); // { a: 1, b: { c: 3 } }
console.log(obj.b.c === newObj.b.c); // true
```

위 코드는 2차원 객체를 newObj에 복사하고, newObj.b.c의 값을 변경하였다. 기존 obj 객체를 출력해보면 newObj.b.c의 값도 3으로 변경되었다. 복사된 하위 객체 { c: 2 }도 결국 객체이기 때문에 얕은 복사가 이루어진 것이다. 이는 Object.assign() 메서드의 한계이며, 전개 연산자(Spread Operator) 를 이용한 객체의 복사에도 같은 문제가 있다.

<br>

#### **Spread 연산자 (전개 연산자)**

전개 연산자를 활용해도 객체의 깊은 복사가 가능하다.

```javascript
const obj = { a: 1 };
const newObj = Object.assign({}, obj);

newObj.a = 2;

console.log(obj); // { a: 1 }
console.log(obj === newObj); // false
```

하지만 Object.assign()와 마찬가지로 2차원 객체는 얕은 복사가 되는 것을 확인할 수 있다.

```javascript
const obj = {
  a: 1,
  b: {
    c: 2,
  },
};

const newObj = { ...obj };

newObj.b.c = 3;

console.log(obj); // { a: 1, b: { c: 3 } }
console.log(obj.b.c === newObj.b.c); // true
```

<br>

### **#2 깊은 복사(Deep Copy)**

깊은 복사된 객체는 객체 안에 객체가 있을 경우에도 원본과의 참조가 완전히 끊어진 객체를 말한다. 복사를 하는 목적은 기존 객체의 값만 복사본으로 가져와 별도로 활용하기 위함이 대부분이다. 기존 객체까지 건드린다면 이것은 복사를 하는 목적에 벗어난다.

- 객체를 복사 할 때, 해당 객체와 인스턴스 변수까지 복사한다.
- 전부를 복사하여 새 주소에 담기 때문에 참조를 공유하지 않는다.
- 객체가 참조 타입의 멤버를 포함할 경우 참조값의 복사가 아닌 참조된 객체 자체가 복사되는 것을 의미한다. 원본의 참조는 더 이상 하지 않는다.

<br>

#### **JSON.parse && JSON.stringify**

JSON.stringify()는 객체를 json 문자열로 변환하는데 이 과정에서 원본 객체와의 참조가 모두 끊어진다.

객체를 json 문자열로 변환 후, JSON.parse()를 이용해 다시 원래 객체(자바스크립트 객체)로 만들어준다.

```javascript
const obj = {
  a: 1,
  b: {
    c: 2,
  },
};

const newObj = JSON.parse(JSON.stringify(obj));

newObj.b.c = 3;

console.log(obj); // { a: 1, b: { c: 2 } }
console.log(obj.b.c === newObj.b.c); // false
```

이 방법이 가장 간단하고 쉽지만 다른 방법에 비해 느리다는 것과 객체가 function일 경우, undefined로 처리한다는 것이 단점이다.
아래의 경우 복사된 newObj는 func가 없고 undefined로 출력되고 있다.

```javascript
const obj = {
  a: 1,
  b: {
    c: 2,
  },
  func: function () {
    return this.a;
  },
};

const newObj = JSON.parse(JSON.stringify(obj));

console.log(newObj.func); // undefined
```

<br>

#### **커스텀 재귀 함수를 구현한 복사**

이 문제를 원칙적으로 해결하려면 직접 깊은 복사를 구현하는 커스텀 재귀 함수를 사용하는 것이다. 복잡하다는 것이 단점이다.

```javascript
function deepCopy(obj) {
  if (obj === null || typeof obj !== "object") {
    return obj;
  }

  let copy = {};
  for (let key in obj) {
    copy[key] = deepCopy(obj[key]);
  }
  return copy;
}

const obj = {
  a: 1,
  b: {
    c: 2,
  },
  func: function () {
    return this.a;
  },
};

const newObj = deepCopy(obj);

newObj.b.c = 3;
console.log(obj); // { a: 1, b: { c: 2 }, func: [Function: func] }
console.log(obj.b.c === newObj.b.c); // false
```

deepCopy 함수의 인수로 obj 객체를 넣었다. 인수값이 객체가 아닌 경우는 그냥 반환하며, 객체인 경우 객체의 값 만큼 루프를 돌며 재귀를 호출하여 복사된 값을 반환한다. 복사된 newObj 객체를 보면 2차원 객체의 값도 깊은 복사가 이루어 졌으며, 객체의 함수도 제대로 표현되는 것을 확인할 수 있다.

<br>

#### **Lodash 라이브러리의 cloneDeep 메소드 사용**

라이브러리를 사용하면 더 쉽고 안전하게 깊은 복사를 할 수 있다. 설치를 해야 한다는 점과 일반적인 개발에는 효율적이겠지만, 코딩 테스트에는 사용할 수 없다는 것이 단점이다.

```javascript
// & npm i lodash 으로 설치
const lodash = require("lodash");

const obj = {
  a: 1,
  b: {
    c: 2,
  },
  func: function () {
    return this.a;
  },
};

const newObj = lodash.cloneDeep(obj);

newObj.b.c = 3;
console.log(obj); // { a: 1, b: { c: 2 }, func: [Function: func] }
console.log(obj.b.c === newObj.b.c); // false
```

<br>

---

<br>

참고자료

1. <a href="https://whales.tistory.com/54" target='_blank'>얕은복사, 깊은복사 알아보기(feat.원시타입, 참조타입)</a>
2. <a href="https://bbangson.tistory.com/78" target='_blank'>[JavaScript] 깊은 복사, 얕은 복사</a>
3. <a href="https://velog.io/@recordboy/JavaScript-%EC%96%95%EC%9D%80-%EB%B3%B5%EC%82%ACShallow-Copy%EC%99%80-%EA%B9%8A%EC%9D%80-%EB%B3%B5%EC%82%ACDeep-Copy" target='_blank'>[JavaScript] 얕은 복사(Shallow Copy)와 깊은 복사(Deep Copy)</a>
