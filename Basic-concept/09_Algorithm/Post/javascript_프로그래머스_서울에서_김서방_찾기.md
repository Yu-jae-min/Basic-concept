# [javascript-algorithm] 프로그래머스 - 서울에서 김서방 찾기

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12919" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12919</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let seoul = ["Jane", "Kim"];

function solution1(seoul) {
  return "김서방은 " + seoul.indexOf("Kim") + "에 있다";
}

console.log(solution1(seoul)); // 김서방은 1에 있다
```

### - 문제해설

> indexOf()메서드를 활용하여 "Kim"의 index값을 찾아낸다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let seoul = ["Jane", "Kim"];

function solution2(seoul) {
  var answer = 0;

  for (var i = 0; i < seoul.length; i++) {
    if (seoul[i] == "Kim") {
      answer = i;
    }
  }
  return "김서방은 " + answer + "에 있다";
}

console.log(solution2(seoul)); // 김서방은 1에 있다
```

### - 문제해설

> 1.  반복문을 활용하는데 배열의 length만큼 반복시키며 i를 증가시킨다.<br>
> 2.  반복문 안에 조건문을 활용하는데 배열의 요소가 Kim인 경우 answer에 i를 할당한다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
let seoul = ["Jane", "Kim"];

const solution3 = (seoul) =>
  `김서방은 ${seoul.findIndex((s) => s === "Kim")}에 있다`;

console.log(solution3(seoul)); // 김서방은 1에 있다
```

### - 문제해설

> findIndex()메서드를 활용하여 s === "Kim"의 조건을 만족하는 첫번째 index값을 찾아낸다.

<br>

## (3) 참고자료

1. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf" target='_blank'>Array.prototype.indexOf()</a><br>
2. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex" target='_blank'>Array.prototype.findIndex()</a>
