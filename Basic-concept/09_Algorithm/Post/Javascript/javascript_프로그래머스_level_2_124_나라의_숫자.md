# [Algorithm] 프로그래머스 Level 2 - 124 나라의 숫자

2023년 10월 04일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/12899

<br>
<br>

# 2. 나의 풀이

```tsx
const mySolution = (n) => {
  var answer = "";
  const arr = ["4", "1", "2"];
  while (n > 0) {
    answer = arr[n % 3] + answer;
    n = Math.floor((n - 1) / 3);
  }

  return answer;
};

console.log(mySolution(5)); // 12
```

1. 규칙을 파악한다. 3진법과 비슷하다. 단 0대신 4가 존재한다. 그렇기 때문에 3으로 나누었을 때 나머지가 0인 경우 4가 되고 아닌 경우 나머지 수 1혹은 2가 된다.
2. 배열 arr을 생성하여 4, 1, 2를 요소로 할당한다.
3. while문을 통해 반복하는데 n이 0보다 큰 경우까지 반복한다.
4. 반복문 내부에서 n을 3으로 나누었을 때 나머지 값을 index로 사용하여 arr 배열 요소의 index로 사용하여 answer에 새로 값을 할당한다. 이 때 기존 앞에 추가되야하므로 기존 answer을 더하여 할당한다.
5. 반복문 내부에서 answer에 새로운 값을 할당한 뒤 n에 다음 계산을 위해 기존 값에 1을 빼준 뒤 3으로 나누어 정수로 변환하여 n에 새로 할당한다.

<br>
<br>

# 3. 인기 풀이

```tsx
const othersSolution = (n) => {
  return n === 0
    ? ""
    : othersSolution(parseInt((n - 1) / 3)) + [1, 2, 4][(n - 1) % 3];
};

console.log(othersSolution(5)); // 12
```

1. 재귀 함수를 활용한다. 이 때 재귀 함수가 리턴하는 값은 n이 0인 경우 빈 문자열, 아닌 경우 재귀 호출한다. 최종 값을 출력할 때 빈 문자열을 반환하는 이유는 배열 내부에 3진수를 문자열로 바꿔주기 위해서이다.
2. 재귀 함수 호출 시 parseInt를 통해 함수로 전달되는 인자를 정수로 바꿔주는데 이 때 현재 n에 1을 뺀 뒤 3으로 나눈 값을 정수로 바꿔주어 전달한다. 이유는 해당 문제의 규칙에서 3으로 나눈 값을 다음 계산에 활용하기 때문이다.
3. 재귀 함수 호출 시 현재 평가 값을 124를 활용한 3진법으로 변환한 값을 더해준다. 이 때 현재 124가 담긴 배열에 현재 n에 1을 빼고 3을 나눈 나머지 값을 index로 활용하여 변환한다. 이유는 나머지가 1이나 2일 때 n에 1을 빼도 결과에 차이가 없기 때문에 코드 통일을 위해서 빼준다.

<br>
<br>

# 4. 비교

해당 문제는 10진수를 다른 진수로 변환할 때 규칙과 비슷했다. 예를 들어 10진수를 2진수로 바꿀 때도 10진수를 0이 될 때 까지 2로 계속 나눈 뒤 나머지를 역순으로 읽어 2진수를 구하는데 이 문제를 예시로 들어보면 이 역순으로 읽는 나머지 값을 특정 3진수가 담긴 배열의 index로 활용할 수 있었다.

즉, 파라미터로 전달받은 10진수를 문제에서 제시하고 있는 것이 3진수로 바꾸는 것인데 3진수이기 때문에 10진수를 3으로 나눈 뒤 나머지에 해당 하는 값은 3진법의 숫자가 담긴 배열의 index로 활용하는 것이다. 또한 나눈 몫은 다음 계산에서 활용하는 방식이다.

나의 풀이의 경우도 방금 설명한 것과 같이 현재 평가 값을 3으로 나눈 뒤 나머지 값을 3진수가 담긴 배열의 index로 활용하였고 다음 사이클에서는 현재 평가 값에 1을 뺀 값을 정수로 변환하여 활용하였다. 인기 풀이의 경우도 거의 비슷했다. 하지만 인기 풀이의 경우 재귀 함수를 활용하여 풀었다.

<br>
