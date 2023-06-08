# [javascript-algorithm] 프로그래머스 - 문자열 내림차순으로 배치하기

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12917" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12917</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let s = "Zdbefcg";

function solution1(s) {
  return s.split("").sort().reverse().join("");
}

console.log(solution1(s)); // gfedcbZ
```

### - 문제해설

> 1.  split()메서드로 문자를 개별로 잘라 배열로 변환하여 담는다.<br>
> 2.  sort()메서드로 문자를 순서대로 정렬한다.<br>
> 3.  reverse()메서드로 문자를 역순으로 뒤집는다.<br>
> 4.  join()메서드로 개별로 분리되어 있는 배열 요소를 하나의 값으로 합쳐준다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let s = "Zdbefcg";

function solution2(s) {
  return s
    .split("")
    .sort((a, b) => (a < b ? 1 : -1))
    .join("");
}

console.log(solution2(s)); // gfedcbZ
```

### - 문제해설

> 1.  split()메서드로 문자를 개별로 잘라 배열로 변환하여 담는다.<br>
> 2.  sort()메서드로 문자를 순서대로 정렬한다. 파라미터값은 삼항연산자를 활용하여 a<b를 비교하고 a가 b보다 크면 -1(음수), b가 a보다 크면 1(양수)를 출력합니다. (a<b의 의미는 오름차순[a-z]을 뜻하다.) sort()메서드의 파라미터값은 음수일 경우 a가 b보다 앞에 오도록 정렬하고, 양수일 경우 b가 a보다 앞에 오도록 정렬한다. 그러므로 오름차순일 경우 양수를 출력하여 순서를 뒤집고, 내림차순일 경우 음수를 출력하여 순서 그대로를 출력하도록 한다.<br>
> 3.  join()메서드로 개별로 분리되어 있는 배열 요소를 하나의 값으로 합쳐준다.

<br>

## (3) 참고자료

1. <a href="https://hianna.tistory.com/409" target='_blank'>Array.prototype.sort()</a>
