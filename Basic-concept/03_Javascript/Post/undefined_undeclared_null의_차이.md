# **undefined / undeclared / null의 차이**

## **# undefined / undeclared / null**

null / unedefined / undeclared의 차이점을 알아보자!

<br>

### **# undefined**

undefined(미정의 변수)는 변수 선언 후 값이 할당되지 않은 상태이다.
타입은 undefined 이다.

```javascript
var test;
console.log(test); // undefined
console.log(typeof test); // undefined
```

<br>

### **# undeclared**

undeclared(미선언 변수)는 변수 선언조차 되지 않은 상태이다.
타입은 undeclared 이다.

```javascript
console.log(test2); // Error!
console.log(typeof test2); // undefined
```

<br>

### **# null**

null(의도적인 빈 값)은 비어있는 값을 할당, 타입은 객체이다.

```javascript
var test3 = null;
console.log(test3); // null
console.log(typeof test3); // object
```
