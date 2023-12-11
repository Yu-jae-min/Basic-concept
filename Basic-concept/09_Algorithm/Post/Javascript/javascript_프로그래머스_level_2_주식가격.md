# [Algorithm] 프로그래머스 Level 2 - 주식가격

2023년 12월 12일

<br>

# 1. 문제

- [https://school.programmers.co.kr/learn/courses/30/lessons/154539](https://school.programmers.co.kr/learn/courses/30/lessons/42584)

<br>
<br>

# 2. 나의 풀이

```tsx
const mySolution = (prices) => {
  const answer = new Array(prices.length).fill(0);

  for (let i = 0; i < prices.length; i++) {
    for (let j = i + 1; j < prices.length; j++) {
      answer[i] += 1;

      if (prices[i] > prices[j]) break;
    }
  }

  return answer;
};

console.log(mySolution([1, 2, 3, 2, 3])); // [4, 3, 1, 1, 0]
```

1. 주식이 떨어지지 않은 시간을 담을 배열 answer을 생성하여 0으로 할당하였다.
2. 반복문을 중첩으로 사용하였는데 내부 반복문에서 기준 요소와 다음 요소들을 반복하여 비교할 때마다 시간을 증가시켰다. 그 후 기준 요소가 비교 요소보다 커지는 경우 내부 반복문을 멈추고 외부 반복문 다음 사이클이 실행되도록 하였다.

<br>
<br>

# 3. 인기 풀이

```tsx
const othersSolution = (prices) => {
  const answer = new Array(prices.length).fill(0);
  const stack = [];
  let length = prices.length;

  for (let i = 0; i < length; i++) {
    while (stack.length && prices[i] < prices[stack[stack.length - 1]]) {
      let temp = stack.pop();
      answer[temp] = i - temp;
    }
    stack.push(i);
  }

  while (stack.length) {
    let temp = stack.pop();
    answer[temp] = length - temp - 1;
  }

  return answer;
};

console.log(othersSolution([1, 2, 3, 2, 3])); // [4, 3, 1, 1, 0]
```

1. 주식이 떨어지지 않은 시간을 담을 배열 answer을 생성하여 0으로 할당하였다. 그 후 stack을 쌓을 배열을 생성하고 주식가격 리스트를 담은 length 변수를 생성하였다.
2. 첫번째 for 반복문에서 주식가격 리스트 길이만큼 반복하는데 반복문 내부에서 stack에 현재 index를 push 한다. 이 때 while문을 활용하여 stack이 있고, 현재 순회 중인 주식가격이 stack에 맨 끝에 삽입된 주식가격보다 작은 경우, 즉 이전 stack에 들어간 index에 해당하는 주식가격이 현재 index에 해당하는 주식가격보다 큰 경우이기 때문에 주식가격이 떨어진 것이므로 stack에 맨 끝 요소 index를 추출하여 answer 배열에 추출한 index 부분에 현재 index와 추출한 index의 차를 구하여 넣는다. 즉 시간차를 구하여 넣는 것과 같다. 이 부분에서는 배열이 끝나기 전 기존 값보다 떨어지는 주식 값을 찾는 것이다.
3. 두번째 while 반복문에서 stack이 있는 경우 순회하는데 stack에 맨 끝 요소 index를 추출하여 answer 배열에 파라미터 길이에 추출한 index를 빼고 다시 1을 더 뺀 값을 구하여 넣는다. 이 부분도 마찬가지로 시간차를 구하여 넣는 것과 같다., 이 부분에서는 배열이 끝날 때까지 떨어지지 않는 주식가격을 구하는 것이다.

<br>
<br>

# 4. 비교

나의 풀이의 경우 O(n2)의 시간 복잡도를 가지고 있다. 그런데 파라미터의 길이는 100,000 이하라는 조건이 있었다. 그렇기 때문에 100,000 \* 100,000이라는 결과가 나올 수도 있었기에 테스트 케이스 및 효율성 테스트가 통과하지 못할 줄 알았다. 하지만 break를 사용한 덕에 모든 테스트를 통과할 수 있었다. 하지만 문제 의도 자체가 스택이나 큐를 사용한 구현을 유도하고 있었다. 이런 부분을 감안하면 의도한 대로 풀이를 하지는 못한 것 같다. 인기 풀이의 경우 stack을 활용하여 풀이하였다. 첫번째 반복문에서 stack에 주식가격의 index를 삽입하며 해당 stack을 활용하여 배열 순회가 끝나기 전 주식가격이 하락하는 요소를 찾아냈고 두번째 반복문에서 stack에 쌓인 요소를 활용하여 배열 순회가 끝날 때까지 주식가격이 하락하지 않는 요소를 찾아냈다. 그 후 시간초를 구하여 정답을 도출해냈다. 인기 풀이를 보며 느낀 점은 stack을 정말 잘 활용했다는 생각이 든다.

<br>
