# [javascript-algorithm] 프로그래머스 - 약수의 합

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12928" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12928</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let n = 12;

function solution1(n) {
  let answer = 0;

  for (let i = 1; i <= n; i++) {
    if (n % i === 0) {
      answer += i;
    }
  }
  return answer;
}

console.log(solution1(n)); // 28
```

### - 문제해설

> 1.  for문으로 n보다 작거나 같을 경우 반복하여 실행한다.<br>
> 2.  for문안에 if문을 사용하여 약수를 찾아내는 조건 n % i === 0 을 통해 약수를 찾아내고 현재 index값을 변수에 누적하여 더해준다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let n = 12;

function solution2(n, answer = 0, i = 1) {
  return i <= n ? solution2(n, n % i === 0 ? answer + i : answer, ++i) : answer;
}

console.log(solution2(n)); // 28
```

### - 문제해설

> 1.  1번 문제풀이와 동일한 방법이지만 삼항연산자와 재귀함수를 활용하였다.<br>
> 2.  재귀함수로 인해 호출스텍으로 쌓인 값은 마지막으로 처리된 값부터 순차적으로 하나씩 더해 값을 출력한다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
let n = 12;

const solution3 = (n) =>
  Array.from(Array(n), (v, i) => i + 1)
    .filter((num) => n % num === 0)
    .reduce((acc, cur) => (acc += cur), 0);

console.log(solution3(n)); // 28
```

### - 문제해설

> 1.  Array.from() 메서드로 배열을 만드는데 배열의 length는 Array(n)만큼 생성한다. 또한 각각의 빈 배열 Array(n)안에 값은 (v, i) => i + 1가 되는데 v는 빈 배열 Array(n)의 각각의 요소를 가리키며 i는 Array(n) 요소 index값을 말한다. index가 1부터 시작해야하므로 index의 1을 더하여 출력한다. 쉬운 예제로는 Array.from([1, 2, 3], x => x + x) 경우 배열 요소 자체가 더해지기 때문에 출력 값이 [2, 4, 6]이 출력되고 Array.from([1, 2, 3], (v, x) => x + x) 경우 배열 요소의 index가 더해지기 떄문에 출력 값이 [0, 2, 4]가 출력된다.<br>
> 2.  Array.filter() 메서드로 약수를 뽑아내는 조건 n % num === 0을 통해 약수를 걸러내어 새로운 배열을 생성한다.<br>
> 3.  약수로 뽑아낸 값을 하나의 값으로 합쳐주기 위해 Array.reduce() 메서드를 활용한다. 누산기 acc의 초기값은 0이기 때문에 0을 넣어주거나, 넣지 않아도 무관하다.

<br>

## (3) 참고자료

1. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/from" target='_blank'>Array.from()</a><br>
2. <a href="https://velog.io/@yoju/JavaScript-%EB%B0%B0%EC%97%B4-%EB%A9%94%EC%86%8C%EB%93%9C-map-filter-find-reduce" target='_blank'>Array.filter()</a><br>
3. <a href="https://velog.io/@yoju/JavaScript-%EB%B0%B0%EC%97%B4-%EB%A9%94%EC%86%8C%EB%93%9C-map-filter-find-reduce" target='_blank'>Array.reduce()</a>
