# **프로토타입(Prototype)**

## **# 프로토타입(Prototype)**

JavaScript는 프로토타입 기반 언어(prototype-based language)이다.
모든 객체들이 메소드와 속성들을 상속 받기 위한 템플릿으로써 자신의 부모 역할을 담당하는 객체인 프로토타입 객체(prototype object)를 가진다는 의미이다.

<br>

### **# 프로토타입 객체**

자바스크립트의 **모든 객체는 자신의 프로토타입 객체를 가리키는 `[[Prototype]]` 인터널 슬롯을 가지고 있으며** 상속을 위해 사용된다. "객체명.`__proto__`"을 통해 접근할 수 있다.

> `__proto__`는 크롬 브라우저에서 사용하는 프로퍼티명이고, ECMA 명세서에는 `[[Prototype]]`이라는 이름으로 사용한다.

```javascript
var student = {
  name: "Jaem",
};

console.log(student.__proto__ === Object.prototype); // true
```

객체를 생성할 때 프로토타입 객체는 결정되며 결정된 프로토타입 객체는 다른 임의의 객체로 변경할 수 있다. 이것은 부모 객체인 프로토타입을 동적으로 변경할 수 있다는 것을 의미한다. 이러한 특징을 활용하여 객체의 상속을 구현할 수 있다.

<br>

### **# `[[Prototype]]` 인터널 슬롯 vs prototype 프로퍼티**

함수도 객체이므로 `[[Prototype]]` 인터널 슬롯을 갖는다. 그런데 함수 객체는 일반 객체와는 달리 **prototype 프로퍼티**도 소유하게 된다.

```javascript
function Person(name) {
  this.name = name;
}

var foo = new Person("Lee");

console.log(Person.prototype); // {constructor: ƒ}
console.log(foo.prototype); // undefined

console.log(Person.__proto__ === Function.prototype); // true
console.log(Person.prototype === foo.__proto__); // true
```

<br>

#### **# `[[Prototype]]`**

- 모든 객체가 가지고 있다
- 객체의 입장에서 자신의 부모 역할을 하는 프로토타입 객체를 가리킨다.

<br>

#### **# prototype 프로퍼티**

- 함수 객체만 가지고 있는 프로퍼티이다.
- 함수 객체의 prototype 프로퍼티에는 constructor 프로퍼티를 담고 있다. 이 constructor 프로퍼티는 자신을 생성한 객체를 가리키게 되는데 prototype 프로퍼티는 함수 객체에 의해 생성되었기 때문에 함수 자신을 가리킨다.
- 내장 함수 객체(Object, Array 등)의 prototype 프로퍼티는 관련 메서드 중 상속하기 위한 메서드를 담고 있다. MDN에서 메서드를 검색해보면 Object.prototype.~, Array.prototype.~과 같은 형태를 볼 수 있는데 이와 같은 이유이다. 또한 내장 함수 객체의 prototype 프로퍼티도 constructor 프로퍼티를 가지고 있다.
- prototype 프로퍼티 또한 객체이므로 `[[Prototype]]` 인터널 슬롯을 가지고 있다. 단 Object.prototype의 경우 프로토체인의 종점이므로 `[[Prototype]]` 인터널 슬롯의 값은 null이다.

> `[[Prototype]]` 인터널 슬롯은 상속을 받기 위한 부모 객체인 프로토타입 객체의 링크를 달아놓는 프로퍼티라면 prototype 프로퍼티는 상속을 하기 위한 메소드 혹은 construct를 가지고 있는 프로퍼티이다.

<br>

#### **# constructor 프로퍼티**

부모 객체인 프로토타입 객체는 prototype 프로퍼티 내부에 constructor 프로퍼티를 갖는다. constructor는 자기 자신을 생성한 객체를 가리키게 되는데 프로토타입 객체의 경우 prototype 프로퍼티를 생성한 객체가 자기 자신이기 때문에 자기 자신을 가리키게 된다.

> 예를 들어 상속을 위한 Person이라는 생성자 함수를 만들게 되면 Person.prototype에는 constructor 프로퍼티가 있다. 이 constructor는 Person을 가리키게 된다. 왜냐하면 Person.prototype는 Person에 의해 생성되었기 때문이다.

이 프로토타입 객체를 상속받는 자식 객체는 프로토타입 객체의 constructor 프로퍼티를 상속받기 때문에 자신이 어떤 객체에 의해 생성되었는지 알 수 있다.

> 예를 들어 Person이라는 생성자 함수를 통해 foo라는 객체를 생성하게 되면 Person.prototype이 foo의 프로토타입 객체이므로 foo의 `__proto__`는 Person.prototype를 가리키게 되며 prototype 프로퍼티 내부에 있는 constructor를 탐색할 수 있게 된다. 그렇기 때문에 foo.constructor를 입력하게 되면 foo가 constructor를 직접 가지고 있는지 확인 후 없기 때문에 `[[Prototype]]`에서 탐색하게 되는 것이다. 그렇게 되면 자신이 어떤 객체에 의해 생성되었는지 알 수 있다.

결론적으로 **constructor 프로퍼티는 프로토타입 객체의 입장에서 자기 자신을 가리키고 객체의 입장에서 자신을 생성한 객체를 가리킨다.**

```javascript
function Person(name) {
  this.name = name;
}

var foo = new Person("Lee");

// Person 생성자 함수에 의해 생성된 객체를 생성한 객체는 Person 생성자 함수이다.
console.log(Person.prototype.constructor === Person); // true

// foo 객체를 생성한 객체는 Person() 생성자 함수이다.
console.log(foo.constructor === Person); // true

// Person 생성자 함수를 생성한 객체는 Function() 생성자 함수이다.
console.log(Person.constructor === Function); // true
```

<br>

### **# 프로토타입 체인**

자바스크립트는 특정 객체의 프로퍼티나 메소드에 접근하려고 할 때 해당 객체에 접근하려는 프로퍼티 또는 메소드가 없다면 `[[Prototype]]` 인터널 슬롯이 가리키는 링크를 따라 자신의 부모 역할을 하는 프로토타입 객체의 프로퍼티나 메소드를 차례대로 검색한다. 이것을 프로토타입 체인(Prototype chain)이라 한다.

```javascript
var student = {
  name: "Lee",
  score: 90,
};

// Object.prototype.hasOwnProperty()
console.log(student.hasOwnProperty("name")); // true
console.log(student.__proto__ === Object.prototype); // true
console.log(Object.prototype.hasOwnProperty("hasOwnProperty")); // true
```

student 객체는 hasOwnProperty 메소드를 가지고 있지 않으므로 에러가 발생하여야 하나 정상적으로 결과가 출력되었다. 이는 student 객체의 `[[Prototype]]`이 가리키는 링크를 따라가서 student 객체의 부모 역할을 하는 프로토타입 객체(Object.prototype)의 메소드 hasOwnProperty를 호출하였기 때문에 가능한 것이다.

> Object나 Array 관련 메서드를 사용할 때에도 결국 Object.property, Array.property가 가지고 있는 메서드를 프로토타입 체인으로 탐색하여 사용하게 되는 것이다.

<br>

### **# 프로토타입 체인의 종점**

Object의 prototype 프로퍼티는 모든 프로토타입 상속 트리의 꼭대기이며 Object의 prototype 프로퍼티를 프로토타입 체인의 종점(End of prototype chain)이라 한다. Object.prototype 프로퍼티는 종점이므로 `[[Prototype]]` 체인이 없다.

```javascript
console.log(Object.prototype.__proto__); // null
console.log(Object.prototype === Function.prototype.__proto__); // true
console.log(Object.prototype === Array.prototype.__proto__); // true
console.log(Object.prototype === Number.prototype.__proto__); // true
```

![javascript_prototype_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/2a27d8e4-3c44-4651-a1e7-d2daeb3c2576)

<br>

### **# 객체 리터럴 방식으로 생성된 객체의 프로토타입 체인**

자바스크립트의 객체 생성 방법은 3가지가 있다.

- 객체 리터럴
- 생성자 함수
- Object() 생성자 함수

```javascript
// 객체 리터럴
var person1 = {
  name: "Lee",
};

// 생성자 함수
function Person(name, gender) {
  this.name = name;
}
var person2 = new Person("Lee", "male"); // 인스턴스 객체의 생성

// Object 생성자 함수
var person3 = new Object(); // 빈 객체의 생성
person4.name = "Lee"; // 프로퍼티 추가
```

객체 리터럴 방식으로 생성된 객체는 내장 함수인 Object() 생성자 함수로 객체를 생성하는 것을 단순화시킨 것이다. Object() 생성자 함수는 물론 함수이므로 prototype 프로퍼티가 있다. 결론적으로 객체 리터럴을 사용하여 객체를 생성한 경우, 그 객체의 프로토타입 객체는 Object.prototype이다.

```javascript
var person = {
  name: "Lee",
  gender: "male",
};

console.log(person.__proto__ === Object.prototype); // true
console.log(Object.prototype.constructor === Object); // true
console.log(Object.__proto__ === Function.prototype); // true
console.log(Function.prototype.__proto__ === Object.prototype); // true
```

![javascript_prototype_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/919da090-f6c8-4c70-8684-8a49cf8c1fc3)

<br>

### **# 생성자 함수로 생성된 객체의 프로토타입 체인**

자바스크립트의 함수 정의 방법은 3가지가 있다.

- 함수선언식(Function declaration)
- 함수표현식(Function expression)
- Function() 생성자 함수

```javascript
// 함수 선언식
function square(number) {
  return number * number;
}

// 함수 표현식
var foo = function multiply(a, b) {
  // 기명 함수 표현식(named function expression)
  return a * b;
};

var bar = function (a, b) {
  // 익명 함수 표현식(anonymous function expression)
  return a * b;
};

// Function() 생성자 함수
var square = new Function("number", "return number * number");
console.log(square(10)); // 100
```

함수선언식의 경우 자바스크립트 엔진이 내부적으로 기명 함수표현식으로 변환한다.
결국 함수선언식, 함수표현식 모두 함수 리터럴 방식을 사용한다. 함수 리터럴 방식은 Function() 생성자 함수로 함수를 생성하는 것을 단순화 시킨 것이다.

즉, 3가지 함수 정의 방식은 결국 Function() 생성자 함수를 통해 함수 객체를 생성한다. 따라서 어떠한 방식으로 함수 객체를 생성하여도 모든 함수 객체의 prototype 객체는 Function.prototype이다. 생성자 함수도 함수 객체이므로 생성자 함수의 prototype 객체는 Function.prototype이다.

```javascript
function Person(name, gender) {
  this.name = name;
  this.gender = gender;
}

var foo = new Person("Lee", "male");

console.log(foo.__proto__ === Person.prototype); // ① true
console.log(Person.prototype.__proto__ === Object.prototype); // ② true
console.log(Person.prototype.constructor === Person); // ③ true
console.log(Person.__proto__ === Function.prototype); // ④ true
console.log(Function.prototype.__proto__ === Object.prototype); // ⑤ true
```

![javascript_prototype_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/1cd7b318-9ae1-4405-b12c-e9162ada0841)

<br>

### **# 프로토타입 객체의 확장**

프로토타입 객체도 객체이므로 일반 객체와 같이 프로퍼티를 추가/삭제할 수 있다. 그리고 이렇게 추가/삭제된 프로퍼티는 즉시 프로토타입 체인에 반영된다.

```javascript
function Person(name) {
  this.name = name;
}

var foo = new Person("Lee");

Person.prototype.sayHello = function () {
  console.log("Hi! my name is " + this.name);
};

foo.__proto__.sayBye = function () {
  console.log("Bye! my name is " + this.name);
};

foo.sayHello(); // Hi! my name is Lee
foo.sayBye(); // Bye! my name is Lee

console.dir(Person.prototype); // sayHello, sayBye가 추가된 것을 확인할 수 있다.
```

생성자 함수 Person은 프로토타입 객체 Person.prototype와 prototype 프로퍼티에 의해 바인딩되어 있다. Person.prototype 객체는 일반 객체와 같이 프로퍼티를 추가/삭제가 가능하다. 위의 예에서는 Person.prototype 객체에 메소드 sayHello를 추가하였다. 이때 sayHello 메소드는 프로토타입 체인에 반영된다. 따라서 생성자 함수 Person에 의해 생성된 모든 객체는 프로토타입 체인에 의해 부모객체인 Person.prototype의 메소드를 사용할 수 있게 되었다.

![javascript_prototype_04](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/8d3641a3-eb18-439c-a458-69bc1a08449d)

<br>

### **# 원시 타입(Primitive data type)의 확장**

자바스크립트에서 원시 타입(숫자, 문자열, boolean, null, undefined)을 제외한 모든것은 객체이다. 그런데 아래 예제를 살펴보면 원시 타입인 문자열이 객체와 유사하게 동작한다.

```javascript
var str = "test";
console.log(typeof str); // string
console.log(str.constructor === String); // true
console.dir(str); // test

var strObj = new String("test");
console.log(typeof strObj); // object
console.log(strObj.constructor === String); // true
console.dir(strObj);
// {0: "t", 1: "e", 2: "s", 3: "t", length: 4, __proto__: String, [[PrimitiveValue]]: "test" }

console.log(str.toUpperCase()); // TEST
console.log(strObj.toUpperCase()); // TEST
```

원시 타입 문자열과 String() 생성자 함수로 생성한 문자열 객체의 타입은 분명이 다르다. 원시 타입은 객체가 아니므로 프로퍼티나 메소드를 가질수 없다. 하지만 원시 타입으로 프로퍼티나 메소드를 호출할 때 원시 타입과 연관된 객체로 일시적으로 변환되어 프로토타입 객체를 공유하게 된다.

원시 타입은 객체가 아니므로 프로퍼티나 메소드를 직접 추가할 수 없다.

```javascript
var str = "test";

// 에러가 발생하지 않는다.
str.myMethod = function () {
  console.log("str.myMethod");
};

str.myMethod(); // Uncaught TypeError: str.myMethod is not a function
```

하지만 String 객체의 프로토타입 객체 String.prototype에 메소드를 추가하면 원시 타입, 객체 모두 메소드를 사용할 수 있다.

```javascript
var str = "test";

String.prototype.myMethod = function () {
  return "myMethod";
};

console.log(str.myMethod()); // myMethod
console.log("string".myMethod()); // myMethod
console.dir(String.prototype);
```

앞서 살펴본 바와 같이 모든 객체는 프로토타입 체인에 의해 Object.prototype 객체의 메소드를 사용할 수 있었다. Object.prototype 객체는 프로토타입 체인의 종점으로 모든 객체가 사용할 수 있는 메소드를 갖는다.

이후 살펴보게 될 Built-in object(내장 객체)의 Global objects (Standard Built-in Objects)인 String, Number, Array 객체 등이 가지고 있는 표준 메소드는 프로토타입 객체인 String.prototype, Number.prototype, Array.prototype 등에 정의되어 있다. 이들 프로토타입 객체 또한 Object.prototype를 프로토타입 체인에 의해 자신의 프로토타입 객체로 연결한다.

자바스크립트는 표준 내장 객체의 프로토타입 객체에 개발자가 정의한 메소드의 추가를 허용한다.

```javascript
var str = "test";

String.prototype.myMethod = function () {
  return "myMethod";
};

console.log(str.myMethod());
console.dir(String.prototype);

console.log(str.__proto__ === String.prototype); // ① true
console.log(String.prototype.__proto__ === Object.prototype); // ② true
console.log(String.prototype.constructor === String); // ③ true
console.log(String.__proto__ === Function.prototype); // ④ true
console.log(Function.prototype.__proto__ === Object.prototype); // ⑤ true
```

![javascript_prototype_05](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/82d84cdb-5b5f-4ff3-b3b8-be6ab93a60ee)

<br>

### **# 프로토타입 객체의 변경**

객체를 생성할 때 프로토타입 객체는 결정되며 결정된 프로토타입 객체는 다른 임의의 객체로 변경할 수 있다. 이것은 부모 객체인 프로토타입을 동적으로 변경할 수 있다는 것을 의미한다. 이러한 특징을 활용하여 객체의 상속을 구현할 수 있다.

이때 주의할 것은 프로토타입 객체를 변경하면

- 프로토타입 객체 **변경 시점 이전에 생성된 객체는 기존 프로토타입 객체를 `[[Prototype]]`에 바인딩**한다.
- 프로토타입 객체 **변경 시점 이후에 생성된 객체는 변경된 프로토타입 객체를 `[[Prototype]]`에 바인딩**한다.

```javascript
function Person(name) {
  this.name = name;
}

var foo = new Person("Lee");

// 프로토타입 객체의 변경
Person.prototype = { gender: "male" };

var bar = new Person("Kim");

console.log(foo.gender); // undefined
console.log(bar.gender); // 'male'

console.log(foo.constructor); // ① Person(name), Person이 생성될 때 가지고 있던 prototype프로퍼티 내부에 constructor프로퍼티를 참조한다.
console.log(bar.constructor); // ② Object(), prototype프로퍼티가 변경되어 변경된 객체는 Object()에 의해 생성되었으므로 constructor는 Object가 된다.
```

![javascript_prototype_06](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/607d79fb-a559-424d-946d-bc122fc36035)

변경 시점 전에 constructor 프로퍼티는 Person() 생성자 함수를 가리킨다. 프로토타입 객체 변경 후, Person() 생성자 함수의 Prototype 프로퍼티가 가리키는 프로토타입 객체를 일반 객체로 변경하면서 Person.prototype.constructor 프로퍼티도 삭제되었다. 따라서 프로토타입 체인에 의해 bar.constructor의 값은 프로토타입 체이닝에 의해 Object.prototype.constructor 즉 Object() 생성자 함수가 된다.

<br>

### **# 프로토타입 체인 동작 조건**

객체의 프로퍼티를 참조하는 경우, 해당 객체에 프로퍼티가 없는 경우, 프로토타입 체인이 동작한다.

객체의 프로퍼티에 값을 할당하는 경우, 프로토타입 체인이 동작하지 않는다. 이는 객체에 해당 프로퍼티가 있는 경우, 값을 재할당하고 해당 프로퍼티가 없는 경우는 해당 객체에 프로퍼티를 동적으로 추가하기 때문이다.

```javascript
function Person(name) {
  this.name = name;
}

Person.prototype.gender = "male"; // ①

var foo = new Person("Lee");
var bar = new Person("Kim");

console.log(foo.gender); // ① 'male'
console.log(bar.gender); // ① 'male'

// 1. foo 객체에 gender 프로퍼티가 없으면 프로퍼티 동적 추가
// 2. foo 객체에 gender 프로퍼티가 있으면 해당 프로퍼티에 값 할당
foo.gender = "female"; // ②

console.log(foo.gender); // ② 'female'
console.log(bar.gender); // ① 'male'
```

![javascript_prototype_07](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/d67fa79a-caae-4cbe-8b93-8d12b7716c33)

foo 객체의 gender 프로퍼티에 값을 할당하면 프로토타입 체인이 발생하여 Person.prototype 객체의 gender 프로퍼티에 값을 할당하는 것이 아니라 foo 객체에 프로퍼티를 동적으로 추가한다.

<br>

### **# 프로토타입 객체를 활용한 상속 예시**

#### **# 예시1 : 중복된 객체의 경우**

```javascript
// 수정 전
const bmw = {
  color: "red",
  wheels: 4,
  navigation: 1,
  drive() {
    console.log("drive..");
  },
};

const benz = {
  color: "black",
  wheels: 4,
  drive() {
    console.log("drive..");
  },
};

const audi = {
  color: "blue",
  wheels: 4,
  drive() {
    console.log("drive..");
  },
};
```

아래와 같이 수정할 수 있다.

```javascript
// 수정 후
const car = {
  wheels: 4,
  drive() {
    console.log("drive..");
  },
};

const bmw = {
  color: "red",
  navigation: 1,
};

const benz = {
  color: "black",
};

const audi = {
  color: "blue",
};

// 프로토타입 객체 변경
bmw.__proto__ = car;
benz.__proto__ = car;
audi.__proto__ = car;

console.log(bmw.wheels); // 4

// 프로토타입 체인
const x5 = {
  color: "white",
  name: "x5",
};

x5.__proto__ = bmw;

console.log(x5.navigation); // 1
```

중복되는 프로퍼티 car객체를 생성하여 car의 프로퍼티로 담아놓았다. 그 후 bmw.`__proto__` = car 로 상속받을 객체의 프로토타입 객체를 car로 변경하여 car의 프로퍼티를 상속받았다.

그 후 bmw.wheels를 콘솔에 찍어보면 car가 가지고 있는 wheels의 value를 출력한다.

또한 x5이라는 새로운 객체를 생성하여 x5.`__proto__` = bmw 로 car를 상속받은 bmw를 프로토타입 객체로 설정하였다. 이렇게 프로토타입은 이어질 수 있다. 이것이 프로토타입 체인이다.

x5를 console.dir로 찍어보면 결과는 아래와 같다.

![javascript_prototype_08](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/80ce26ab-a8e1-4dc9-a191-a60cf7437df8)

자기 자신이 가지고 있는 프로퍼티부터 bmw가 가지고 있는 프로퍼티, car가 가지고 있는 프로퍼티, Object가 가지고 있는 프로퍼티로 이어지는 것을 확인할 수 있다.

```javascript
for (p in x5) {
  console.log(p); // color name navigation wheels drive
}

console.log(Object.keys(x5)); // ['color', 'name']
```

또한 위와 같이 for in문은 프로토타입 체인으로 모든 프로퍼티를 탐색하며 Object.keys와 같이 값과 관련된 메서드는 직접 가지고 있는 메서드로만 탐색한다. 잘 구분해서 사용하여야한다.

<br>

#### **# 예시2 : 생성자 함수 사용**

```javascript
// 수정 전
const car = {
  wheels: 4,
  drive() {
    console.log("drive..");
  },
};

const Bmw = function (color) {
  this.color = color;
};

const x5 = new Bmw("red");
const z4 = new Bmw("blue");

x5.__proto__ = car;
z4.__proto__ = car;

console.log(x5.wheels); // 4
```

위의 코드는 예시1과 같이 상속받을 객체의 프로토타입 객체를 수정하는 방법이다. 하지만 객체가 여러개인 경우 반복적으로 수행해야된다. 이러한 경우 아래의 방법으로 극복할 수 있다.

```javascript
// 수정 후
const Bmw = function (color) {
  this.color = color;
};

Bmw.prototype.wheels = 4;
Bmw.prototype.drive = function () {
  console.log("drive..");
};

const x5 = new Bmw("red");
const z4 = new Bmw("blue");

console.log(x5.wheels); // 4
```

위와 같이 상속받을 객체 x5, z4의 프로토타입 객체를 car로 수정하는 방법이 아닌, 프로토타입 객체 Bmw에 직접 프로퍼티를 추가하여 자식 객체 x5, z4가 이 값을 참조할 수 있게 하였다. 이 같은 방법을 활용하면 여러개의 자식 객체가 생성되더라도 프로토타입 객체의 프로퍼티를 참고하므로 추가 작업이 필요하지 않다.

추가로 위와 같이 프로토타입 객체의 prototype 프로퍼티를 나누어 할당할 수 있지만 아래와 같이 한번에 프로퍼티를 추가하는 것도 가능하다. 하지만 아래와 같은 경우 constructor가 사라지기 때문에 위와 같이 나누어 할당하는 것이 좋은 방법이다.

만약 그래도 수정 후와 같은 방법을 사용한다면 Bmw.prototype 객체 내부에 "constructor: Bmw" 라는 프로퍼티를 추가해주면 constructor가 설정된다.

```javascript
// 수정 전
Bmw.prototype.wheels = 4;
Bmw.prototype.drive = function () {
  console.log("drive..");
};

const x5 = new Bmw("red");
const z4 = new Bmw("blue");

console.log(x5.wheels); // 4
console.log(x5.constructor === Bmw); // true, 좋은 방법
```

```javascript
// 수정 후
Bmw.prototype = {
  // constructor: Bmw, // constructor를 직접 설정하여 삭제되는 현상을 방지할 수 있다.
  wheels: 4,
  drive() {
    console.log("drive..");
  },
};

const x5 = new Bmw("red");
const z4 = new Bmw("blue");

console.log(x5.wheels); // 4
console.log(x5.constructor === Bmw); // false, 나쁜 방법
```

<br>

#### **# 예시3 : 생성자 함수의 클로저**

```javascript
// 수정 전
const Bmw = function (color) {
  this.color = color;
};

const x5 = new Bmw("red");
x5.color = "black";

console.log(x5.color); // black
```

아래와 같이 클로저를 활용하여 외부에서 값에 접근만 할 뿐 수정할 수 없게 만들 수 있다.

```javascript
// 수정 후
const Bmw = function (color) {
  const c = color;
  this.getColor = function () {
    console.log(c);
  };
};

const x5 = new Bmw("red");
// x5.color = 'black'; // 에러!

x5.getColor(); // red
```

<br>

---

<br>

참고자료

- <a href="https://poiemaweb.com/js-prototype" target='_blank'>프로토타입</a>
- <a href="https://poiemaweb.com/es6-class" target='_blank'>클래스</a>
- <a href="https://poiemaweb.com/js-object-oriented-programming" target='_blank'>자바스크립트 객체지향 프로그래밍</a>
- <a href="https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Object_prototypes" target='_blank'>Object prototypes</a>
- <a href="https://www.youtube.com/watch?v=4_WLS9Lj6n4" target='_blank'>자바스크립트 중급 강좌</a>
- <a href="https://ko.javascript.info/native-prototypes" target='_blank'>내장 객체의 프로토타입</a>
- <a href="https://ko.javascript.info/function-prototype" target='_blank'>함수의 prototype 프로퍼티</a>
