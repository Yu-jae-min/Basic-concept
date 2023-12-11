# **[Algorithm] 프로그래머스 Level 1 - 예산**

2023년 07월 27일

<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/12982

<br>
<br>

## **2. 나의 풀이**

```jsx
const mySolution = (d, budget) => {
  var answer = 0;
  let currentBudget = budget;
  const sortAsc = d.sort((a, b) => a - b);

  sortAsc.forEach((requiredBudget) => {
    if (requiredBudget <= currentBudget) {
      currentBudget = currentBudget - requiredBudget;
      answer++;
    }
  });

  return answer;
};

console.log(mySolution([1, 3, 2, 5, 4], 9));
```

1. 예산을 `copyBudget` 변수로 복제하였다.
2. 최대한 많은 부서를 지원해야하므로 적은 예산부터 지원하기 위해 `sort` 메소드를 사용하여 오름차순으로 정렬하였다.
3. `forEach` 메소드를 사용하여 현재 예산이 필요한 예산보다 같거나 많을 경우 현재 예산에서 필요 예산을 제외하고 다시 현재 예산 변수에 할당하였다.
4. 그 후 지원한 횟수를 카운트하기 위해 `answer` 변수를 증가시켰다.

<br>
<br>

## **3. 다른 개발자 분의 풀이**

```jsx
const othersSolution = (d, budget) => {
  d.sort((a, b) => a - b);

  console.log(d);

  while (d.reduce((a, b) => a + b, 0) > budget) d.pop();

  return d.length;
};

console.log(othersSolution([1, 3, 2, 5, 4], 9));
```

1. 최대한 많은 부서를 지원해야하므로 적은 예산부터 지원하기 위해 `sort` 메소드를 사용하여 오름차순으로 정렬하였다.
2. `while` 문을 사용하여 조건이 참인 경우 반복하였는데 이 때 조건은 sorting한 배열의 합이 예산보다 많은 경우, 즉 지원이 가능한 경우까지만 반복하였다.
3. 반복문 내부에서는 최대한 많은 부서를 지원해야하므로 필요한 예산이 큰 부서부터 `pop` 메서드를 사용해 배열에서 제거하였다

<br>
