# [javascript-algorithm] 프로그래머스 - 정수 내림차순으로 배치하기

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12933" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12933</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let n = 118372;

const solution = (n) =>
  Number(n.toString().split("").sort().reverse().join(""));

console.log(solution(n)); // 873211
```

### - 문제해설

> 1.  toString 으로 숫자열을 문자열로 바꿔준다.<br>
> 2.  split 으로 문자열을 각각 나누어 배열로 넣는다.<br>
> 3.  sort 로 배열을 오름차순으로 정렬한다.<br>
> 4.  reverse 로 오름차순인 배열을 뒤집어 내림차순으로 정렬한다.<br>
> 5.  join 으로 나누어진 배열의 원소를 하나의 원소로 합친다.<br>
> 6.  Number() 로 다시 숫자열로 바꿔준다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let n = 118372;

function solution(n) {
  const newN = n + "";
  const newArr = newN.split("").sort().reverse().join("");

  return +newArr;
}

console.log(solution(n)); // 873211
```

### - 문제해설

> - 해설은 위와 동일하다. 단 형변환의 방법의 차이점이 있다. 1차적으로 ""를 이용하여 자료형타입을 Number타입에서 String타입으로 변환하였으며 2차적으로 반환되는 값에 +를 이용하여 String타입에서 Number타입으로 변환하였다.

<br>

## (3) 참고자료

1. <a href="https://hianna.tistory.com/377" target='_blank'>String.prototype.split()</a><br>
2. <a href="https://hianna.tistory.com/409" target='_blank'>Array.prototype.sort()</a><br>
3. <a href="https://hianna.tistory.com/448" target='_blank'>Array.prototype.reverse()</a><br>
4. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/join" target='_blank'>Array.prototype.join()</a>
