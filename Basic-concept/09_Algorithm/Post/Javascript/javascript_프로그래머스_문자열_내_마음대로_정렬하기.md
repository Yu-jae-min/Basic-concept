# [javascript-algorithm] 프로그래머스 - 문자열 내 마음대로 정렬하기

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12915" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12915</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let strings = ["sun", "bed", "car"];
let n = 1;

function solution1(strings, n) {
  strings.sort(function (a, b) {
    let first = a[n];
    let second = b[n];
    if (first === second) {
      return (a > b) - (a < b);
    } else {
      return (first > second) - (first < second);
    }
  });
  return strings;
}

console.log(solution1(strings, n)); // ['car', 'bed', 'sun']
```

### - 문제해설

> 1.  n번째 배열을 나누어 담는다.<br>
> 2.  sort()메서드에 비교함수를 만들어 비교한다. n번쨰 문자열이 같은 경우 a,b로 받은 문자열 전체를 비교한다. a>b조건이 true(1)면 a<b조건은 false(0)가 되어 최종적으로 1을 반환하고, a>b조건이 false(0)면 a<b조건은 true(1)가 되어 -1을 반환한다.<br>
> 3.  n번째 문자열이 다른 경우 n번째 문자열을 비교하여 순서를 변경한다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let strings = ["sun", "bed", "car"];
let n = 1;

function solution2(strings, n) {
  return strings.sort((s1, s2) =>
    s1[n] === s2[n] ? s1.localeCompare(s2) : s1[n].localeCompare(s2[n])
  );
}

console.log(solution2(strings, n)); // ['car', 'bed', 'sun']
```

### - 문제해설

> 1.  삼항연산자를 이용하여 조건은 n번째 문자열이 같은 경우를 비교한다.<br>
> 2.  localeCompare()메서드로 결과 값을 반환하는데 조건이 true인 경우 문자열 전체를 비교한다. 양 쪽 문자열을 비교하여 오름차순이면 음수(-1), 내림차순이면 양수(1), 같을 경우 0을 반환한다.<br>
> 3.  localeCompare()메서드로 반환 값이 false일 경우 n번째 문자열을 비교하여 음수 혹은 양수 혹은 0을 반환한다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
let strings = ["sun", "bed", "car"];
let n = 1;

function solution3(strings, n) {
  return strings
    .map((a) => [...a][n] + a)
    .sort()
    .map((a) => a.substring(1));
}

console.log(solution3(strings, n)); // ['car', 'bed', 'sun']
```

### - 문제해설

> 1.  map()메서드로 각각의 배열 요소를 배열요소의 n번째 + 배열요소로 변환시켜준다. (['usun', 'ebed', 'acar'])<br>
> 2.  변환시킨 배열 요소들을 sort()메서드를 활용하여 아스키코드 오름차순으로 정렬시켜준다. (['acar', 'ebed', 'usun'])<br>
> 3.  map()메서드와 substring()메서드를 활용하여 각각의 배열 요소 문자열의 index 1번째부터 시작하는 문자열로 변환시켜준다.

<br>

## (3) 참고자료

1. <a href="https://hianna.tistory.com/374" target='_blank'>비교함수</a><br>
1. <a href="https://noirstar.tistory.com/359" target='_blank'>sort() 알고리즘</a><br>
1. <a href="https://velog.io/@young_mason/Algorithm-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-Sorting-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-Basic%ED%8E%B8" target='_blank'>sorting 알고리즘</a><br>
1. <a href="https://opentutorials.org/course/50/91" target='_blank'>String.prototype.localeCompare()</a>
