# [javascript-algorithm] 프로그래머스 - 나누어 떨어지는 숫자 배열

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12910" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12910</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let arr = [36, 1, 2, 3];
let divisor = 2;

function solution1(arr, divisor) {
  let answer = [];

  for (let i = 0; i < arr.length; i++) {
    if (arr[i] % divisor == 0) answer.push(arr[i]);
  }

  return answer.length == 0 ? [-1] : answer.sort((a, b) => a - b);
}

console.log(solution1(arr, divisor)); // [2, 36]
```

### - 문제해설

> 1.  나누어떨어지는 배열을 담기 위한 빈 배열을 answer에 할당한다.<br>
> 2.  for문을 통해 arr.length보다 작을 때 반복시킨다.<br>
> 3.  if문을 사용하여 arr[i]를 divisor로 나누었을 때 나머지가 0인 경우 push()메서드를 활용하여 나누어 떨어지는 배열 요소를 answer에 추가한다.<br>
> 4.  나누어떨어지는 요소가 하나도 없는 경우 -1을 리턴해야하므로 삼항연산자를 활용하여 answer.length가 0인 경우 [-1]을 리턴하는 조건을 만든다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let arr = [36, 1, 2, 3];
let divisor = 2;

function solution2(arr, divisor) {
  var answer = arr.filter((v) => v % divisor == 0);
  return answer.length == 0 ? [-1] : answer.sort((a, b) => a - b);
}

console.log(solution2(arr, divisor)); // [2, 36]
```

### - 문제해설

> 1.  filter()메서드를 통해 조건을 통과하는 배열 요소들만을 모아 새로운 배열을 생성한다.<br>
> 2.  조건을 통과하는 배열이 존재하지 않아 배열이 비어있는 경우 삼항연산자를 활용하여 [-1]을 리턴한다.<br>
> 3.  배열이 비어있지 않은 경우는 담긴 배열 요소들을 sort()메서드를 활용하여 오름차순으로 리턴한다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
let arr = [36, 1, 2, 3];
let divisor = 2;

function solution3(arr, divisor) {
  var answer = [];

  arr.map((a) => {
    a % divisor === 0 && answer.push(a);
  });

  return answer.length ? answer.sort((a, b) => a - b) : [-1];
}

console.log(solution3(arr, divisor)); // [2, 36]
```

### - 문제해설

> 1.  나누어떨어지는 배열을 담기 위한 빈 배열을 answer에 할당한다.<br>
> 2.  map()메서드를 활용한다. 또한 논리연산자를 활용하여 조건을 만족하는 경우 빈 배열 answer에 해당 배열요소가 push되도록 한다.<br>
> 3.  0이 아닌 경우 true이므로 answer.length로 작성하여 조건식을 만들고 조건을 통과하는 경우 오름차순으로 배열을 정렬한다.<br>
> 4.  조건을 통과하지 못하는 경우 [-1]을 리턴한다.

<br>

## (3) 참고자료

1. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/filter" target='_blank'>Array.prototype.filter()</a><br>
2. <a href="https://velog.io/@proshy/JS%EC%9E%98%EB%AA%BB-%EC%95%8C%EA%B3%A0-%EC%9E%88%EC%97%88%EB%8D%98-%EB%85%BC%EB%A6%AC%EC%97%B0%EC%82%B0%EC%9E%90" target='_blank'>잘못 알고 있었던 논리연산자</a>
