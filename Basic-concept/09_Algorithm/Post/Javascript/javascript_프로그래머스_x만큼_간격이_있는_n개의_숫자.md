# [javascript-algorithm] 프로그래머스 - x만큼 간격이 있는 n개의 숫자

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12954" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12954</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let x = 2;
let n = 5;

function solution(x, n) {
  let answer = [];

  for (var i = 1; i <= n; i++) {
    answer.push(x * i);
  }

  return answer;
}

console.log(solution(x, n)); // [2, 4, 6, 8, 10]
```

### - 문제해설

> 1.  빈 배열 answer을 만든다.<br>
> 2.  for문을 이용하여 n만큼 반복하는 반복문을 만든다. 1부터 n까지 x에 곱져야하므로 조건은 i <= n 가 되고 그 후 push() 메서드를 사용하여 곱해진 값을 answer 배열의 워소로 넣어준다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let x = 2;
let n = 5;

function solution(x, n) {
  return Array(n)
    .fill(x)
    .map((v, i) => (i + 1) * v);
}

console.log(solution(x, n)); // [2, 4, 6, 8, 10]
```

### - 문제해설

> 1.  Array 생성자 함수를 사용하여 배열을 생성한다. 이 때 매개변수로 n이 전달되었는데 Array 생성자 함수는 매개변수가 1개이고 이것이 숫자일 때 이 숫자를 length 값으로 가지는 배열을 생성한다. 그러므로 n 만큼의 length 값을 가지는 배열이 생성된다.<br>
>
> - 매개변수가 1개를 초과할 때는 전달 된 매개변수를 원소로 하는 배열을 생성한다.<br>
>
> 2.  fill 메서드를 이용하여 Array 생성자 함수를 사용하여 만든 배열을 전달된 매개변수로 채운다.<br>
> 3.  map 메서드는 배열내의 모든 요소에 해당 연산을 적용시켜 새로운 배열을 생성한다. 여기서 v는 요소값, i는 인덱스값이며 해당 연산을 적용한 새로운 배열이 생성된다.

<br>

## (3) 참고자료

1. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/push" target='_blank'>Array.prototype.push()</a><br>
2. <a href="https://poiemaweb.com/js-array" target='_blank'>Array() 생성자 함수</a><br>
3. <a href="https://velog.io/@colki/JS-Array-%EB%A9%94%EC%84%9C%EB%93%9C-fill" target='_blank'>Array.prototype.fill()</a><br>
4. <a href="https://velog.io/@yoju/JavaScript-%EB%B0%B0%EC%97%B4-%EB%A9%94%EC%86%8C%EB%93%9C-map-filter-find-reduce" target='_blank'>Array.prototype.map()</a>
