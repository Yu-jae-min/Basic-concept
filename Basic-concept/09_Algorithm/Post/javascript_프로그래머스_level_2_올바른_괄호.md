# [Algorithm] 프로그래머스 Level 2 - 올바른 괄호

2023년 09월 28일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/12909

<br>
<br>

# 2. 나의 풀이

## 2-1. 나의 풀이 (1)

```tsx
// 테스트 케이스 통과, 효율성 테스트 1, 2 실패
const mySolution = (s) => {
  const stack = [];
  const queue = [...s];

  queue.forEach((el) => {
    stack.push(el);

    if (
      stack.lastIndexOf("(") >= 0 &&
      stack[stack.lastIndexOf("(") + 1] === ")"
    ) {
      stack.pop();
      stack.pop();
    }
  });

  return !stack.length;
};

console.log(mySolution("()()")); // true
```

1. 빈 배열 stack과 파라미터로 전달받은 s 문자열이 담긴 queue를 생성한다.
2. queue를 forEach로 반복하는데 lastIndexOf를 활용하여 문자열 `(` 의 맨 끝 index를 찾은 뒤 해당 index의 다음 index가 `)` 인 경우 pop 메소드를 사용하여 stack 담긴 요소를 제거하였다.
3. 최종적으로 stack의 length가 남아있는 경우 false, 비어있는 경우 true를 반환하도록 하였다.

<br>

## 2-2. 나의 풀이(2)

```jsx
// 테스트 케이스 통과, 효율성 테스트 통과
const mySolution = (s) => {
  const stack = [];
  const queue = [...s];

  queue.forEach((el) => {
    stack.push(el);

    const isLeftParenthesis = stack[stack.length - 2] === "(";
    const isRightParenthesis = stack[stack.length - 1] === ")";
    const isPerpectParenthesis = isLeftParenthesis && isRightParenthesis;

    if (isPerpectParenthesis) {
      stack.pop();
      stack.pop();
    }
  });

  return !stack.length;
};

console.log(mySolution("()()")); // true
```

1. 빈 배열 stack과 파라미터로 전달받은 s 문자열이 담긴 queue를 생성한다.
2. queue를 forEach로 반복하는데 stack의 length를 활용하여 stack의 맨 끝에서 두번 째 요소가 문자열 `(` 이고 맨 끝 요소가 `)` 인 경우 pop 메소드를 사용하여 stack 담긴 요소를 제거하였다.
3. 최종적으로 stack의 length가 남아있는 경우 false, 비어있는 경우 true를 반환하도록 하였다.

<br>
<br>

# 3. 인기 풀이

```tsx
const othersSolution = (s) => {
  let cum = 0;

  for (let paren of s) {
    cum += paren === "(" ? 1 : -1;

    if (cum < 0) return false;
  }

  return cum === 0 ? true : false;
};

console.log(othersSolution("()()")); // true
```

1. 문자열을 평가하여 숫자를 증감시킬 변수 cum을 생성하였다.
2. 전달받은 문자열 파라미터 s를 for of문으로 반복하는데 현재 반복되고 있는 요소가 문자열 `(` 인 경우 cum에 1을 누적하여 더해주고, `)` 인 경우 1을 누적하여 빼준다. 만약 cum이 음수가 된다면 괄호를 닫을 수 없기 때문에 false를 반환하여 반복문을 종료한다.
3. 최종적으로 cum이 0인 경우 모든 괄호를 닫을 수 있기 때문에 true를 반환하고 아닌 경우 false를 반환한다.

<br>
<br>

# 4. 비교

우선 해당 문제는 스택/큐 문제로 제시되어 있다. 그래서 선입선출의 자료구조인 큐와 후입선출의 자료구인 스택을 활용하는 것이 주요해보였다. 그래서 나의 풀이의 경우 첫번째 풀이는 큐에 파라미터로 전달받은 문자열을 쌓은 뒤 해당 큐를 반복문으로 돌려 큐 내부 요소들이 선입선출 되도록 하였다. 이 때 선입선출 된 요소들은 스택에 쌓이고 lastIndexOf 메소드를 활용하여 괄호를 닫을 수 있는지 끝 요소들 부터 평가하였다. 해당 풀이의 경우 테스트 케이스는 모두 통과하였지만 효율성 테스트에서 실패하였다. 실패한 이유는 아마 시간복잡도 때문에 실패한 것 같다. 반복문 내부에서 index를 찾는 메소드를 사용하여 시간복잡도가 O(n2)가 되어 실패한 것 같았다. 그래서 수정한 것이 두번째 풀이이다. 두번째 풀이도 첫번째 풀이와 거의 비슷하지만 stack의 length를 통해 뒤에 있는 요소들을 평가하였다. 수정한 결과 테스트 케이스와 효율성 테스트 모두 통과할 수 있었다. 인기 풀이의 경우는 number 타입의 변수를 생성한 후 더하고 빼는 방식을 활용하여 구현하였다. push나 pop보다 해당 연산이 더 가볍기 때문에 좋은 풀이인 것 같다. 나의 경우 스택이나 큐 자료구조를 사용해서 구현해야할 때 무조건 빈 배열부터 만들고 생각하는데 인기 풀이와 같이 간단한 연산을 통해 구현할 수 있다면 굳이 배열을 사용할 필요가 없다고 느꼈다.

<br>
