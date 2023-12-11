# [javascript-algorithm] 프로그래머스 - 정수 제곱근 판별

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12934" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12934</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let n = 121;

function solution(n) {
  var result = 0;
  var nSqrt = Number(Math.sqrt(n));

  if (nSqrt % 1 === 0) {
    result = Math.pow(nSqrt + 1, 2);
  } else {
    result = -1;
  }

  return result;
}

console.log(solution(n)); // 144
```

### - 문제해설

> 1.  nSqrt변수에 Math.sqrt()함수로 n의 제곱근을 구한 뒤 숫자형으로 바꾸어 할당한다.<br>
> 2.  if문을 활용한다. 조건은 나누는 기준이 정수이기 때문에 nSqrt값을 1로 나누었을 때 나머지가 0인 경우를 조건으로 넣는다.<br>
> 3.  true일 경우 nSqrt+1 한 값을 제곱해야하므로 Math.pow()함수를 활용한다. 첫번째 파라미터값이 nSqrt+1, 두번째 파라미터값은 2제곱이므로 2를 넣어준다.<br>
> 4.  false일 경우 -1 출력한다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let n = 121;

function solution(n) {
  var result = 0;
  var nSqrt = Math.sqrt(n);

  result = Number.isInteger(nSqrt) ? Math.pow(nSqrt + 1, 2) : -1;

  return result;
}

console.log(solution(n)); // 144
```

### - 문제해설

> 1.  nSqrt변수에 Math.sqrt()함수로 n의 제곱근을 구하여 할당한다.<br>
> 2.  삼항연산자를 활용하는데, 이 중 좌항 조건은 나누는 기준이 정수이기 때문에 정수를 판별하는 Number.isInteger() 메서드를 활용한다. 이 메서드는 정수일 경우 true, 정수가 아닐 경우 false를 반환한다.<br>
> 3.  ture일 경우 nSqrt+1 한 값을 제곱해야하므로 Math.pow()함수를 활용한다. 첫번째 파라미터값이 nSqrt+1, 두번째 파라미터값은 2제곱이므로 2를 넣어준다.<br>
> 4.  false일 경우 -1 출력한다.

<br>

## (3) 참고자료

1. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/sqrt" target='_blank'>Math.sqrt()</a><br>
2. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/pow" target='_blank'>Math.pow()</a><br>
3. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/isInteger" target='_blank'>Number.isInteger()</a>
