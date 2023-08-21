# **[Algorithm] 프로그래머스 Level 1 - 햄버거 만들기**

2023년 08월 21일

<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/133502

<br>
<br>

## **2. 나의 풀이**

```tsx
const mySolution = (ingredient) => {
  var answer = 0;

  while (ingredient.join("").includes("1231")) {
    const burgerIdx = ingredient.join("").indexOf("1231");

    answer++;
    ingredient.splice(burgerIdx, 4);
  }

  return answer;
};

console.log(mySolution([2, 1, 1, 2, 3, 1, 2, 3, 1])); // 2
```

위 코드는 includes 메소드를 사용해서 파라미터로 전달받은 배열 내부에 햄버거를 만들 수 있는 string이 포함되어 있는지 확인 후 포함되어 있다면 반복문을 돌려 햄버거 string의 index를 찾고 그 index를 기준으로 string을 잘라내고 카운트를 증가시키는 방식으로 작성하였다. 위 코드는 테스트 케이스 3-9, 11, 12에서 시간 초과가 발생하였다.

```tsx
const mySolution = (ingredient) => {
  var answer = 0;
  const stack = [];

  ingredient.forEach((ingredientItem) => {
    stack.push(ingredientItem);

    const hasFourItems = stack.length >= 4;
    const hasBurger = stack.slice(-4).join("") === "1231";

    if (hasFourItems && hasBurger) {
      stack.splice(-4);
      answer++;
    }
  });

  return answer;
};

console.log(mySolution([2, 1, 1, 2, 3, 1, 2, 3, 1])); // 2
```

나의 두번째 풀이이다. stack을 추가하고 해당 stack에 파라미터로 전달받은 햄버거 재료를 순차적으로 push하고 최근에 push한 햄버거 재료들로 햄버거를 만들 수 있을 때 해당 재료들을 splice로 잘라내고 카운트를 증가시키는 방식으로 작성하였다.

<br>
<br>

## **3. 인기 풀이**

```tsx
function othersSolution(ingredient) {
  let stk = [];
  let count = 0;
  for (let i = 0; i < ingredient.length; i++) {
    stk.push(ingredient[i]);
    if (
      stk[stk.length - 1] === 1 &&
      stk[stk.length - 2] === 3 &&
      stk[stk.length - 3] === 2 &&
      stk[stk.length - 4] === 1
    ) {
      count++;
      stk.splice(-4);
    }
  }
  return count;
}

console.log(othersSolution([2, 1, 1, 2, 3, 1, 2, 3, 1])); // 2
```

나의 두번째 풀이와 비슷한 풀이이다. 파라미터로 전달받은 배열 요소 길이만큼 반복문을 돌리는데 이 때 햄버거 재료를 배열에 순차적으로 쌓아올리고 가장 최근 재료 4가지로 햄버거를 만들 수 있을 때 카운트를 증가시키고 splice로 해당 재료들을 제거하는 방식으로 작성되었다.

<br>
<br>

## **4. 비교**

우선 프로그래머스 레벨 1의 문제들을 풀다보니 딱히 시간 복잡도에 대해 고민해볼 이유가 없었다. 즉 문제를 해결하기만 한다면 시간 초과가 발생하는 경우가 거의 없었다. 하지만 이번 문제는 달랐다. 나의 풀이 중 첫번째 풀이에서 문제를 해결하였지만 3-9, 11, 12번 테스트 케이스에서 시간 초과가 발생하였다. 그래서 두번째 나의 풀이와 인기 풀이처럼 스택을 구현하여 해결할 수 있었다.

일단 나의 풀이 중 첫번째 풀이의 시간 복잡도는 `O(n^2)`이다. 이유는 while문의 조건 중 전달받은 파라미터 배열을 includes로 테스트하는 부분이 있는데 이 부분에서 우선 `O(n)`의 시간 복잡도가 발생한다. 그 후 while문 내부에서 indexOf를 활용하여 햄버거가 포함되는지 확인하는데 이 때 `O(n)`의 시간 복잡도가 발생하며 결과적으로 `O(n^2)`의 시간 복잡도가 발생한다.

다음 나의 두번째 풀이와 인기 풀이의 시간 복잡도는 `O(n)`이다. 이유는 전달받은 파라미터를 forEach로 반복하는데 이 때 `O(n)`의 시간 복잡도가 발생한다. 그 후 반복문 내부에서 push, slice, splice 등을 활용하는데 이 메소드들의 시간 복잡도는 `O(1)`이다. 그러므로 최종 시간 복잡도는 `O(n)`이다.

결론적으로 나의 첫번째 풀이와 두번째 풀이를 비교해보면 두번째 풀이가 더 효율적인 것을 알 수 있다. 두번째 풀이의 경우 각 요소를 순차적으로 처리하면서 현재까지 스택에 저장된 요소를 이용해 조건을 검사하고 필요한 경우 상수 작업 시간 메소드를 통해 요소를 제거하였다. 이로 인해 중복된 작업을 피하면서 정답을 구할 수 있었다.

하지만 나의 첫번째 풀이의 경우 매 반복이 실행될 때마다 햄버거 문자열이 포함되어있는지를 검사하고 내부에서는 다시 그 전체 문제 중 가장 첫번째 햄버거의 인덱스를 구하는 작업이 수행되므로 시간 복잡도가 증가하는 것을 볼 수 있다. 그러므로 두번째 풀이가 상대적으로 비효율적인 것을 알 수 있다.

<br>
