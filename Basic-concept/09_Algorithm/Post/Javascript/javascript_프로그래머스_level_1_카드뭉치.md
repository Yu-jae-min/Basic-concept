# **[Algorithm] 프로그래머스 Level 1 - 카드뭉치**

2023년 06월 29일

<br>

## **1. 문제**

<a href="https://school.programmers.co.kr/learn/courses/30/lessons/159994" target='_blank'>https://school.programmers.co.kr/learn/courses/30/lessons/159994</a>

<br>
<br>

## **2. 풀이**

```jsx
const cards1 = ["i", "drink", "water"];
const cards2 = ["want", "to"];
const goal = ["i", "want", "to", "drink", "water"];

const solution = (cards1, cards2, goal) => {
  const copyCards1 = [...cards1];
  const copyCards2 = [...cards2];

  const validationArray = goal.map((el) => {
    if (el === copyCards1[0]) {
      copyCards1.shift();
      return "Yes";
    }
    if (el === copyCards2[0]) {
      copyCards2.shift();
      return "Yes";
    }

    return "No";
  });

  return validationArray.includes("No") ? "No" : "Yes";
};

console.log(solution(cards1, cards2, goal)); // result : "Yes"
```

1. 원본 배열을 복사한다. (`copyCards1`, `copyCards2`)
2. 기준이 되는 배열에서 `map()`를 사용하여 복사한 카드 배열의 첫번째 요소와 일치하는지 확인한 후 일치하면 복사한 배열의 첫번째 요소를 제거하고 `“Yes”`를 반환하게 하고 일치하지 않으면 `“No”`를 반환하게 한다.
3. `map()`를 사용하여 변형시킨 변수의 `“No”`가 포함되는지 `includes()`로 확인한다. `“No”`가 포함되는 경우 `“No”`를 반환하고 포함되지 않는 경우 `“Yes”`를 반환한다.

<br>
