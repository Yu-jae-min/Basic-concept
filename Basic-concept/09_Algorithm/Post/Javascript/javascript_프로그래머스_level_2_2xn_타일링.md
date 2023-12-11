# [Algorithm] 프로그래머스 Level 2 - 2 x n 타일링

2023년 10월 05일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/12900

<br>
<br>

# 2. 나의 풀이

```tsx
const mySolution = (n) => {
  const fibonacci = [1, 1, 2];

  if (n == 1) return 1;
  if (n == 2) return 2;

  for (let i = fibonacci.length; i <= n; i++) {
    const nextNum = (fibonacci[i - 1] + fibonacci[i - 2]) % 1000000007;

    fibonacci.push(nextNum);
  }

  return fibonacci[n];
};

console.log(mySolution(4)); // 5
```

1. 규칙을 파악한다. 타일 가로 길이인 n이 1인 경우 경우의 수는 1개, 2인 경우 경우의 수는 2개, 3인 경우 경우의 수는 3개, 4인 경우 경우의 수는 5개 순으로 증가하는 것을 볼 수 있다. 이 규칙에서 알 수 있는 점은 피보나치 수열임을 알 수 있다. n+1번째 항 더하기 n+2번째 항은 n 3번째 항이 되는 것이다.
2. 우선 피보나치 수열을 저장하기 위한 배열 fibonacci을 생성한다. 그 후 피보나치 수열 구현 시 1번째 값과 2번째 값은 미리 초기화하여 구현할 수 있기 때문에 초기화 값 1, 1, 2를 넣어준다.
3. if문을 통해 만약 n이 1이거나 2인 경우 해당 값을 출력하도록 한다.
4. for문으로 반복하는데 3부터 반복해야하기 때문에 초기 값은 미리 생성한 배열의 길이로 지정하고 해당 값이 n보다 작거나 같은 경우까지 반복한다. 이 때 반복문 내부에서는 다음 수 계산을 위해 현재 index에 1을 뺀 요소와 2를 뺀 요소의 값을 합친 뒤 문제에서 제시한 값이 커지는 것을 방지하기 위해 1000000007로 나누어 나머지 값을 구하여 다음 수를 구한다. 그 후 nextNum 변수에 할당하고 해당 값을 fibonacci 배열에 push한다.
5. 최종적으로 피보나치 수열이 저장 된 배열의 끝 수만 출력하면 되기 때문에 배열 fibonacci의 n번째 요소를 출력한다.

<br>
<br>

# 3. 인기 풀이

```tsx
const othersSolution = (n) => {
  const arr = [0, 1, 2];

  for (let i = 3; i <= n; i++) {
    arr[i] = (arr[i - 2] + arr[i - 1]) % 1000000007;
  }

  return arr[n];
};

console.log(othersSolution(4)); // 5
```

나의 풀이와 비슷하다.

<br>
<br>

# 4. 비교

해당 문제는 피보나치 수열을 미리 알았다면 매우 구현하기 쉬웠을 것 같다. 하지만 해당 문제를 풀며 처음에는 피보나치 수열을 떠올리지 못했다. 그래서 프로그래머스 질문하기 페이지에서 힌트를 얻었고 그로 인해 구현할 수 있었다. 이러한 문제들을 효율적으로 구현하기 위해서는 사전 지식이 필요하다는 것을 느꼈다.

<br>
