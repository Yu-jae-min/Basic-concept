# [javascript-algorithm] 프로그래머스 - 콜라츠 추측

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12943" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12943</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let n = 6;

function solution1(num) {
  let answer = 0;

  for (let i = 0; i < 500; i++) {
    if (num != 1) {
      num = num % 2 == 0 ? num / 2 : num * 3 + 1;
    } else {
      return (answer = i);
    }
  }

  return (answer = -1);
}

console.log(solution1(n)); // 8
```

### - 문제해설

> 1.  반복문을 통해 조건 중 500번까지만 반복하는 조건을 설정한다.<br>
> 2.  반복문 안에 조건문을 활용하여 출력값이 1인 경우와 1이 아닌 경우로 나누는데 출력값이 1이 아닌 경우는 연산을 진행 후 할당, 1인 경우는 현재 횟수를 출력한다.<br>
> 3.  500번 반복한 후 return 값이 없는 경우 -1을 할당하여 리턴한다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
function solution2(num) {
  let answer = 0;

  while (num != 1 && answer != 500) {
    num % 2 == 0 ? (num = num / 2) : (num = num * 3 + 1);
    answer++;
  }

  return num == 1 ? answer : -1;
}

console.log(solution2(n)); // 8
```

### - 문제해설

> 1.  반복문에 논리연산자를 활용하여 1이 아닐 때, 500번 반복했을 때의 두 가지 조건을 설정한다.<br>
> 2.  두 가지 조건이 모두 true일 경우 연산을 진행하고 변수 answer을 증감하여 횟수를 저장한다.<br>
> 3.  출력값이 1이 되거나 500번 이상 실행이 될 경우 반복문을 빠져나와 출력값을 출력한다. 이 때 삼항연산자를 활용하는데 조건은 결과값이 1인 경우로 설정한다. 1일 경우 연산 횟수인 answer을 출력하고 1이 아닐 경우 -1을 출력한다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
function solution3(num, count = 0) {
  return num == 1
    ? count >= 500
      ? -1
      : count
    : solution3(num % 2 == 0 ? num / 2 : num * 3 + 1, ++count);
}

console.log(solution3(n));
```

### - 문제해설

> 1.  삼항연산자를 사용하여 num이 1일 때와 1이 아닐때로 조건을 나눈다.<br>
> 2.  true일 경우 count값을 비교하여 500번 이상일 때 -1, 아닐 때 count값을 출력한다.<br>
> 3.  false일 경우 재귀함수를 활용하는데 매개변수로 삼항연산자를 활용하여 연산하며 카운터를 증감시킨다.

<br>

## (3) 참고자료

1. <a href="https://velog.io/@daybreak/Javascript-%EC%82%BC%ED%95%AD%EC%97%B0%EC%82%B0%EC%9E%90" target='_blank'>?(삼항연산자)</a><br>
2. <a href="https://velog.io/@jakeseo_me/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EA%B0%9C%EB%B0%9C%EC%9E%90%EB%9D%BC%EB%A9%B4-%EC%95%8C%EC%95%84%EC%95%BC-%ED%95%A0-33%EA%B0%80%EC%A7%80-%EA%B0%9C%EB%85%90-23-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9E%AC%EA%B7%80Recursion-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0" target='_blank'>재귀함수</a>
