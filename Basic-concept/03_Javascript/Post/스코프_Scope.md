# **# 스코프(Scope)**

## **# 스코프(Scope)**

스코프(Scope)는 변수의 유효 범위를 말한다.

<br>

### **# 스코프의 구분**

- 전역 스코프 (Global scope) : 전역에서 참조할 수 있다.
- 지역 스코프 (Local scope or Function-level scope) : 함수 코드 블록이 만든 스코프로 함수 자신과 하위 함수에서만 참조할 수 있다.

모든 변수는 스코프를 갖는다. 변수의 관점에서 스코프를 구분하면 아래와 같다.

- 전역 변수 (Global variable) : 전역에서 참조할 수 있는 변수이다.
- 지역 변수 (Local variable) : 지역내에서 선언된 변수이며 그 지역과 그 지역의 하부 지역에서만 참조할 수 있는 변수이다.

<br>

### **# 함수 레벨 스코프 / 블록 레벨 스코프**

- 함수 레벨 스코프(function-level scope) : 함수 코드 블록 내에서 선언된 변수는 함수 코드 블록 내에서만 유효하고 함수 외부에서는 유효하지 않다.
- 블록 레벨 스코프(block-level scope) : 블록 레벨 스코프란 코드 블록({…})내에서 유효한 스코프를 의미한다. 함수나 조건문 코드 블록 또한 블록 레벨 스코프이다.

  ```javascript
  function test() {
    var a = 10; // 함수 레벨 스코프
    console.log(a);
  }
  console.log(test()); // 10
  console.log(a); // 에러!
  ```

  위와 같이 var는 함수 레벨 스코프, 아래와 같이 let과 const는 블록 레벨 스코프이다.

  ```javascript
  if (true) {
    const a = 10; // 블록 레벨 스코프
    console.log(a); // 10
  }

  console.log(a); // 에러!
  ```

<br>

### **# 렉시컬 스코프(Lexical scope)**

렉시컬 스코프는 함수를 어디서 호출하는지가 아니라 어디에 선언하였는지에 따라 결정된다.

```javascript
var x = 1;

function foo() {
  var x = 10;
  bar();
}

function bar() {
  console.log(x);
}

foo(); // 1
bar(); // 1
```

<br>

---

<br>

참고자료

- <a href="https://poiemaweb.com/js-scope" target='_blank'>스코프</a>
