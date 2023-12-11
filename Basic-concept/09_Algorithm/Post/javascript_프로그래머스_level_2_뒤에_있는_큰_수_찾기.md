# [Algorithm] 프로그래머스 Level 2 - 뒤에 있는 큰 수 찾기

2023년 12월 11일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/154539

<br>
<br>

# 2. 나의 풀이

```tsx
// 테스트케이스 20~24 시간초과
const mySolution = (numbers) => {
  const answer = [];
  let isChange = false;

  for (let i = 0; i < numbers.length; i++) {
    for (let j = i + 1; j < numbers.length; j++) {
      if (numbers[i] >= numbers[j]) {
        isChange = false;
        continue;
      }

      answer.push(numbers[j]);
      isChange = true;
      break;
    }

    if (!isChange) {
      answer.push(-1);
    }
  }

  return answer;
};

console.log(mySolution([9, 1, 5, 3, 6, 2])); // [-1, 5, 6, 6, -1, -1]
```

1. 뒤 큰수를 담을 배열 answer과 큰수의 여부를 체크하는 플래그 isChange 변수를 생성하였다.
2. 중첩 반복문 중 내부 반복문에서 초기 값을 현재 index의 1을 더한 값으로 지정하여 자기 자신의 비교는 건너뛰고 자기 자신과 다음 값을 비교하는데 자기 자신보다 큰 값이 아닌 경우 변화가 없는 것이기 때문에 isChange를 false로 변경하고 다음 사이클로 넘어가도록 하였다. 만약 뒤 큰수가 있는 경우 answer에 해당 변수를 push한 후 isChange를 true로 바꾸고 내부 반복문을 중지하고 외부 반복문의 다음 사이클이 실행되도록 하였다.
3. 만약 내부 중첩문을 순회하며 뒤 큰수를 못찾는 경우 플래그를 체크하여 answer에 -1을 push 하도록 하였다.

<br>
<br>

# 3. 인기 풀이

```tsx
const othersSolution = (numbers) => {
  const length = numbers.length;
  const answer = Array.from({ length }, () => -1);
  const stack = [];

  for (let i = length - 1; i >= 0; i--) {
    while (stack.length !== 0 && numbers[i] >= stack.at(-1)) stack.pop();

    if (stack.length !== 0) answer[i] = stack.at(-1);

    stack.push(numbers[i]);
  }

  return answer;
};

console.log(othersSolution([9, 1, 5, 3, 6, 2])); // [-1, 5, 6, 6, -1, -1]
```

1. 파라미터 배열의 length를 담은 length 변수, 파라미터 배열 요소 개수만큼 -1을 담은 배열 answer, 순회 중인 요소 및 다음 순회 대상과 비교할 요소를 담을 요소를 담을 stack 변수 생성
2. for문으로 반복문을 돌리는데 뒤에서 부터 순회, 이 때 반복문 내부에서는 스택이 비어있지 않고 현재 요소가 맨 끝 요소보다 크거나 같은 경우, 즉 이전 stack에 들어있는 값이 뒤 큰수가 아닌 경우 제거
3. 반복문 내부 if문에서 stack이 비어있지 않은 경우 현재 answer 배열 내부 요소의 현재 index 위치를 stack에 맨 끝 값으로 할당, 즉 현재 값에 뒤 큰수가 stack에 있으므로 해당 값을 할당하는 것이다.
4. while문과 if문 종료 시 push 메소드를 통해 현재 요소를 stack에 넣는다.

<br>
<br>

# 4. 비교

나의 풀이의 경우 O(n2)의 시간 복잡도를 가지고 있기 때문에 테스트케이스 20~24에서 시간초과가 발생하였다. 인기 풀이의 경우 현재 요소와 비교되는 대상들을 stack에 쌓아두고 비교하는데 stack 쌓이는 기준이 뒤 큰수인지를 판별한 후 제거해버린다. 이런 식으로 동작하여 최소한의 비교를 통해 결과를 만들어냈다.

<br>
