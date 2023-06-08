# **함수 호출 방법 Call by value & call by Reference**

## **# Call by value(값에 의한 호출)**

인자로 원시 타입의 객체를 넘기는 것을 말한다. 함수의 파라미터는 인자와 같은 데이터의 주소 값을 참조하고 있지만 함수 내부에서 파라미터를 수정하는 경우 콜스택에서 새로운 데이터를 생성하여 그 데이터의 주소 값을 참조하기 때문에 원본의 변화는 없다. 값을 복사하여 처리하기 때문에 안전하고 원래의 값이 보존되지만 메모리 사용량이 늘어난다.

```js
// Call by value(값에 의한 호출)
const a = 1;

const callByValue = (param) => {
  param = 2;

  return param;
};

console.log(callByValue(a)); // 2
console.log(a); // 1, 원본 변경 X
```

<br>

## **# Call by reference(참조에 의한 호출)**

인자로 참조 타입의 객체를 넘기는 것을 말한다. 함수의 파라미터는 인자와 같은 데이터의 주소 값을 참조하고 있어 함수 내부에서 파라미터를 수정하는 경우 원본이 변화된다. 복사하지 않고 직접 참조를 하기에 처리가 빠르지만 원본의 변화가 생길 수 있다.

```js
// Call by reference(참조에 의한 호출)
const arr = [1, 2, 3];

const callByReference = (param) => {
  param.push(4);

  return param;
};

console.log(callByReference(arr)); // [1, 2, 3, 4]
console.log(arr); // [1, 2, 3, 4], 원본 변경 O
```

<br>
