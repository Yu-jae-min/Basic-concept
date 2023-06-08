# [javascript-algorithm] 프로그래머스 - 두 정수 사이의 합

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12912" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12912</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let a = 3;
let b = 5;

function solution1(a, b) {
  let answer = 0;

  for (i = Math.min(a, b); i <= Math.max(a, b); i++) answer += i;

  return answer;
}

console.log(solution1(a, b)); // 12
```

### - 문제해설

> 1.  for문을 활용하여 반복시킨다. i 초기값을 Math.min()함수로 a, b의 최소값으로 할당한다. 또한 종료조건은 Math.max()함수로 a, b의 최대값으로 할당한다.<br>
> 2.  반복문이 반복될 떄마다 answer에 i를 누적하며 더하며 할당하다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let a = 3;
let b = 5;

function solution2(a, b) {
  var answer = 0;

  return ((a + b) * (Math.abs(b - a) + 1)) / 2;
}

console.log(solution2(a, b)); // 12
```

### - 문제해설

> 등차수열의 합(가우스 공식)을 활용하여 계산한다. 등차수열의 합을 구할 때는 첫항과 마지막항을 더해서 항수를 곱하고 2로 나눈다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
let a = 3;
let b = 5;

function solution3(a, b) {
  var answer = a < b ? a : b;

  while (a != b) {
    answer += a < b ? ++a : ++b;
  }

  return answer;
}

console.log(solution3(a, b)); // 12
```

### - 문제해설

> 1.  삼항연산자를 활용하여 answer변수에 두 수의 최소 값을 할당한다.<br>
> 2.  while문을 활용한다. 조건식은 a가 b와 같지 않을 때 반복하여 실행한다.<br>
> 3.  첫번째 사이클에서 ++a로 인해 증감한 4가 더해지면서 할당되고, 다음 사이클에서 ++a로 인해 증감한 5가 더해지면서 할당된다.

<br>

## (3) 참고자료

1. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/min" target='_blank'>Math.min()</a><br>
2. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/max" target='_blank'>Math.max()</a><br>
3. <a href="https://m.blog.naver.com/seekhim/222280134895" target='_blank'>등차수열의 합(가우스 공식)</a><br>
4. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/abs" target='_blank'>Math.abs()</a>
