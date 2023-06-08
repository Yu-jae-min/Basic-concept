# this

## **# this**

**this**란 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수(self-reference variable)이다. 자바스크립트 엔진에 의해 암묵적으로 생성되며 객체의 프로퍼티나 메서드를 참조하기 위한 자기 참조 변수이므로 일반적으로 객체의 메서드 내부 또는 생성자 함수 내부에서만 의미가 있다.

<br>

### **# 전역객체**

```javascript
console.log(this); // Window

var ga = "Global variable";

console.log(ga); // Global variable
console.log(window.ga); // Global variable

function foo() {
  console.log("invoked!");
}
window.foo(); // invoked!
```

전역객체는 모든 객체의 유일한 최상위 객체를 의미하며 일반적으로 Browser-side에서는 window, Server-side(Node.js)에서는 global 객체를 의미한다.

또한, 전역객체는 전역 스코프를 갖는 전역변수를 프로퍼티로 소유한다. 글로벌 영역에 선언한 함수는 전역객체의 프로퍼티로 접근할 수 있는 전역 변수의 메소드이다.

<br>

### **# 함수의 this**

```javascript
function aOuter() {
  console.log(this); // Window, strict모드 시 undefined

  function aInner() {
    console.log(this); // Window, strict모드 시 undefined
  }
  aInner();
}
aOuter();
```

기본적으로 this는 전역객체(Global object)에 바인딩된다. 전역함수는 물론이고 심지어 내부함수의 경우도 this는 외부함수가 아닌 전역객체에 바인딩된다.

```javascript
var value = 1;

var obj = {
  value: 100,
  foo: function () {
    setTimeout(function () {
      console.log("3. 콜백함수: ", this); // window
    }, 0);
  },
};

obj.foo();
```

콜백함수의 경우에도 this는 전역객체에 바인딩된다.
내부함수는 일반 함수, 메소드, 콜백함수 어디에서 선언되었든 관게없이 this는 전역객체를 바인딩한다.

<br>

### **# 객체의 메소드 this**

객체의 프로퍼티의 value값이 함수일 경우 메서드라고 한다.

```javascript
var obj = {
  a: function () {
    // 객체의 메서드(일반함수)
    var that = this;
    console.log(this); // {a: ƒ, b: ƒ}

    function aInner() {
      // 객체의 메서드(일반함수)의 내부함수
      console.log(this); // Window
      console.log(that); // {a: ƒ, b: ƒ}
    }
    aInner();
  },
  b: () => {
    // 객체의 메서드(화살표함수)
    console.log(this); // window

    function bInner() {
      // 객체의 메서드(화살표함수)의 내부함수
      console.log(this); // Window
    }
    bInner();
  },
};

obj.a();
obj.b();

// 객체의 메소드를 새로운 변수에 할당하는 경우
var a2 = obj.a;
a2(); // window
window.a2(); // window
```

위와 같이 메서드 내부에 새로운 변수 that에 this를 할당하여 메서드의 내부 함수가 전역객체에 바인딩되는 것을 막을 수 있다. aInner함수에 메서드 내부에 생성한 that을 활용한다.

또한, 위와 같이 객체의 메소드를 새로운 변수에 할당하는 경우 호출하는 시점에 this는 Window로 변경된다. 이유는 변수 a2는 obj의 프로퍼티가 아닌 전역객체의 프로퍼티이기 때문이다. (변수 a2는 메모리힙에 저장되는 obj.a의 주소 값을 참조하는 것일 뿐이다.)

<br>

### **# 생성자 함수의 this**

자바스크립트의 생성자 함수는 말 그대로 객체를 생성하는 역할을 한다. 기존 함수에 new 연산자를 붙여서 호출하면 해당 함수는 생성자 함수로 동작한다.

생성자 함수가 아닌 일반 함수에 new 연산자를 붙여 호출하면 생성자 함수처럼 동작할 수 있다. 따라서 일반적으로 생성자 함수명은 첫문자를 대문자로 기술하는 컨벤션이 있다.

```javascript
// 생성자 함수
function Person(name) {
  this.name = name;
}

Person.prototype.getName = function () {
  return this.name;
};

var me = new Person("Lee"); // new 연산자 사용
console.log(me); // Person {name: 'Lee'}

var you = Person("Kim"); // new 연산자 미사용
console.log(you); // undefined

console.log(me instanceof Person); // true
console.log(me.getName()); // Lee

Person.prototype.name = "Kim";
console.log(Person.prototype.getName()); // Kim
```

- Person.prototype.getName와 같이 프로토타입 객체 메소드 내부에서 사용된 this도 일반 메소드 방식과 마찬가지로 해당 메소드를 호출한 객체에 바인딩된다.
- 변수 you와 같이 new 연산자와 함께 생성자 함수를 호출하지 않으면 생성자 함수로 동작하지 않는다.
- 변수 me는 Person의 인스턴스이다. 생성자 함수의 this는 자신이 생성할 인스턴스를 가리키기 때문에 me를 가리키게 된다.

<br>

### **# 함수 메서드 bind, call, apply**

일반 함수의 경우 bind, call, apply 함수 메서드를 통해 명시적으로 this를 바꿀 수 있다.

```javascript
// 일반 함수
var obj2 = { c: "d" };
function b() {
  console.log(this);
}
b(); // Window
b.bind(obj2).call(); // obj2
b.call(obj2); // obj2
b.apply(obj2); // obj2

// 화살표 함수
var obj3 = { c: "d" };
var c = () => {
  console.log(this);
};
c(); // Window
c.bind(obj3).call(); // Window
c.call(obj3); // Window
c.apply(obj3); // Window
```

bind, call, apply의 기능은 비슷하지만 아래와 같은 차이점이 있다.

- bind : 첫번째 파라미터로 this바인딩 결정, 두번째 파라미터부터 함수에 인자 전달, 함수는 실행하지 않음
- call : 첫번째 파라미터로 this바인딩 결정, 두번째 파라미터부터 함수에 인자 전달 (인자를 각각 전달), 함수 실행
- apply : 첫번째 파라미터로 this바인딩 결정, 두번째 파라미터부터 함수에 인자 전달 (인자를 배열로 전달), 함수 실행

또한 위와 같이 화살표 함수는 this 바인딩을 제공하지 않는다. 동적으로 변경되는 일반 this와 다르게 정적으로 this가 결정되며 this는 언제나 상위 스코프의 this를 가리킨다.

> **일반 함수 vs 화살표 함수**
>
> - this 바인딩 방식 : 일반 함수는 호출 방식에 따라 this가 결정되고, 화살표 함수는 언제나 상위 스코프 this를 가리킨다.
> - 생성자 함수로 사용 가능 여부 : 일반 함수는 생성자 함수로 사용 가능하지만 화살표 함수는 생성자 함수로 사용할 수 없다. 왜냐하면 prototype 프로퍼티를 가지고 있지 않기 때문이다.
> - arguments 객체 : 함수 생성 시 일반 함수에는 암묵적으로 arguments 객체가 전달되며 화살표 함수에서는 arguments 객체가 전달되지 않는다.

<br>

---

<br>

참고자료

- <a href="https://poiemaweb.com/js-this" target='_blank'>함수 호출 방식에 의해 결정되는 this</a>
- <a href="https://hanamon.kr/javascript-this%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%BC%EA%B9%8C/" target='_blank'>[JavaScript] this 란 무엇일까?</a>
