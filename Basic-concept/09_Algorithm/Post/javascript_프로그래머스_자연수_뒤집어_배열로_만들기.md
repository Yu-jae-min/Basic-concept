# [javascript-algorithm] 프로그래머스 - 자연수 뒤집어 배열로 만들기

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12932" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12932</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let n = 12345;

const solution1 = (n) =>
  n
    .toString()
    .split("")
    .map((str) => Number(str))
    .reverse();

console.log(solution1(n)); // [5, 4, 3, 2, 1]
```

### - 문제해설

> 1.  toString() 메서드로 숫자형을 문자형으로 바꾸어준다.<br>
> 2.  split() 메서드로 문자형을 나누어 배열에 담는다.<br>
> 3.  map() 메서드로 개별로 나누어진 문자형들을 돌면서 숫자형으로 바꾸어준다.<br>
> 4.  reverse() 메서드로 배열의 순서를 반전한다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let n = 12345;

function solution2(n) {
  let answer = [];

  do {
    answer.push(n % 10);
    n = Math.floor(n / 10);
  } while (n > 0);

  return answer;
}

console.log(solution2(n)); // [5, 4, 3, 2, 1]
```

### - 문제해설

> 1.  arr변수에 빈 배열을 할당한다.<br>
> 2.  do-while문을 활용한다. 이 때 조건은 n>0일 때 까지만 반복한다.<br>
> 3.  push()메서드를 활용하는데 n%10 나머지 값을 넣어준다.
>     (사이클 순서대로 5(12345를 10으로 나눈 나머지 값) -> 4(1234를 10으로 나눈 나머지값) -> 3(123을 10으로 나눈 나머지값) -> 2(12를 10으로 나눈 나머지 값) -> 1(1을 10으로 나눈 나머지 값))<br>
> 4.  n변수에 Math.floor()을 활용하여 값을 할당하는데 n/10을 매개변수로 하여 소수점 자리를 버린 수를 할당한다.
>     (사이클 순서대로 1234(1234.5의 소수점 버린 수) -> 123(123.4의 소수점 버린 수) -> 12(12.3의 소수점 버린 수) -> 1(1.2의 소수점 버린 수) -> 0(0.1의 소수점 버린 수))<br>
> 5.  값이 할당된 변수 answer 출력한다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
let n = 12345;

function solution3(n) {
  let nStr = n.toString();
  let answer = [];

  for (let i = nStr.length - 1; i >= 0; i--) {
    answer.push(Number(nStr[i]));
  }

  return answer;
}

console.log(solution3(n)); // [5, 4, 3, 2, 1]
```

### - 문제해설

> 1.  toString() 메서드로 숫자형을 문자형으로 바꾸어 nStr변수에 할당한다.<br>
> 2.  answer변수에 빈 배열을 할당한다.<br>
> 3.  for반복문을 활용하는데 순서를 반전해야하므로 nStr의 변수 length -1부터 반복문을 시작하며 i가 0보다 크거나 같을 경우 반복하여 실행한다. 또한 index값이 줄어야하므로 증감연산자 i-- 를 활용하여 i값을 감소시킨다.<br>
> 4.  반복문안에 push() 메서드로 반전한 문자열을 answer변수에 순차적으로 할당하는데 Number()함수를 활용하여 숫자형으로 바꾸어 할당한다.<br>
> 5.  값이 할당된 변수 answer를 출력한다.

<br>

## (3) 참고자료

1. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/do...while" target='_blank'>do...while</a><br>
2. <a href="https://tonks.tistory.com/138" target='_blank'>Math.floor()</a>
