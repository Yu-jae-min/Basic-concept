# [javascript-algorithm] 프로그래머스 - 문자열 다루기 기본

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12918" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12918</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let s = "1234";

function solution1(s) {
  return s.length === 4 || s.length === 6 ? !isNaN(s) : false;
}

console.log(solution1(s)); // true
```

### - 문제해설

> 1.  삼항연산자를 활용하는데 문자의 길이가 4 혹은 6 일 때를 조건으로 한다.<br>
> 2.  문자의 길이가 4 혹은 6 일 때, isNaN()함수를 이용하여 NaN(Not a Number)를 판별하는데 isNaN()함수는 매개변수가 숫자가 아닐 경우 ture, 숫자일 경우 false를 반환하므로 !를 붙여 반대의 결과를 출력하도록 한다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let s = "1234";

function solution2(s) {
  const len = s.length;

  if (len === 4 || len === 6) {
    return s.split("").every((c) => !isNaN(c));
  }

  return false;
}

console.log(solution2(s)); // true
```

### - 문제해설

> 1.  문자의 길이가 4혹은 6일 때의 조건문을 만든다.<br>
> 2.  split()메서드로 문자를 개별로 나눈 뒤 배열로 만든다.<br>
> 3.  every()메서드로 각각의 배열 요소를 함수로 판별하는데, 판별하는 조건으로 isNaN()함수를 이용한다. isNaN()함수를 통해 배열안의 모든 요소가 true일 경우에만 true를 출력한다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
let s = "1234";

function solution3(s) {
  return (s.length === 4 || s.length === 6) && /^[0-9]+$/.test(s);
}

console.log(solution3(s)); // true
```

### - 문제해설

> 1.  논리연산자 &&(AND)를 활용하여 값을 출력한다. 첫번째 조건은 문자의 길이가 4혹은 6일 때의 조건을 설정한다.<br>
> 2.  두번째 조건은 정규식을 활용한다. ^(시작), [0-9](0~9까지의 숫자), +(반복, 앞의 문자가 1개 이상인 경우), $(종료)로 작성한다. 또한 test()메서드를 활용하여 설정해놓은 정규식안에 매개변수의 문자가 포함되는지를 판별한다. 포함되면 true, 포함되지 않으면 false를 반환한다.

<br>

## (3) 참고자료

1. <a href="https://ko.javascript.info/logical-operators" target='_blank'>논리연산자</a><br>
2. <a href="https://www.codingfactory.net/10383" target='_blank'>isNaN()</a><br>
3. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/every" target='_blank'>Array.prototype.every()</a><br>
4. <a href="https://runebook.dev/ko/docs/javascript/global_objects/regexp/test" target='_blank'>RegExp.prototype.test()</a>
