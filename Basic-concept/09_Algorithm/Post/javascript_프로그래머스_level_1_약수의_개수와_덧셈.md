# **[Algorithm] 프로그래머스 Level 1 - 약수의 개수와 덧셈**

2023년 08월 02일

<br>
<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/77884

<br>
<br>

## **2. 나의 풀이**

```tsx
const mySolution = (left, right) => {
  var answer = 0;

  for (let i = left; i <= right; i++) {
    let count = 0;

    for (let j = 1; j <= i; j++) {
      if (i % j === 0) count++;
    }

    if (count % 2 === 0) {
      answer += i;
    } else {
      answer -= i;
    }
  }

  return answer;
};

console.log(mySolution(13, 17));
```

1. 주어진 파라미터의 사이 수 만큼 반복문을 돌렸다.
2. 반복문 내부에서 반복문을 중첩으로 사용하여 1부터 현재 사이클의 i값까지 반복문을 돌렸다. 이 때 i값을 j로 나누었을 때 나머지가 0인 경우, 즉 약수인 경우 카운트를 증가시켰다.
3. 그 후 첫번째 반복문이 다음 사이클로 넘어가기 전 카운트 값을 2로 나누어 홀짝을 판별하고 짝수인 경우 answer에 해당 값을 더하고 홀수인 경우 뺏다.

<br>
<br>

## **3. 인기 풀이**

```tsx
const othersSolution = (left, right) => {
  var answer = 0;

  for (let i = left; i <= right; i++) {
    if (Number.isInteger(Math.sqrt(i))) {
      answer -= i;
    } else {
      answer += i;
    }
  }

  return answer;
};

console.log(othersSolution(13, 17));
```

1. 주어진 파라미터의 사이 수 만큼 반복문을 돌렸다.
2. 반복문 내부에서 현재 사이클 값의 `Math.sqrt` 메소드를 활용하여 제곱근을 구하고 `Number.isInteger` 메소드를 통해 정수인지 판별하였다.
3. 이 때 판별한 값이 정수인 경우 약수의 개수가 홀수이므로 answer에 해당 빼고 아닌 경우 뺏다.

나의 풀이의 경우 단순하게 반복문을 중첩해서 해결하였지만 인기 풀이의 경우 제곱근이 정수면 약수의 개수가 홀수라는 점을 활용해서 반복문을 중첩해서 사용하지 않았다.

<br>
