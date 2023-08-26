# **[Algorithm] 프로그래머스 Level 1 - 명예의 전당 1**

2023년 08월 26일

<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/138477

<br>
<br>

## **2. 나의 풀이**

```jsx
const mySolution = (k, score) => {
  const lowestScores = [];
  const hallOfFameScores = [];

  score.forEach((currentScore) => {
    hallOfFameScores.push(currentScore);

    if (hallOfFameScores.length > k) {
      const lowestScoreIndex = hallOfFameScores.indexOf(
        Math.min(...hallOfFameScores)
      );
      hallOfFameScores.splice(lowestScoreIndex, 1);
    }

    const lowestScore = Math.min(...hallOfFameScores);
    lowestScores.push(lowestScore);
  });

  return lowestScores;
};

console.log(mySolution(3, [10, 100, 20, 150, 1, 100, 200])); // [10, 10, 10, 20, 20, 100, 100]
```

1. stack을 쌓기 위한 빈 배열 `hallOfFameScores`, 일별 최저 점수 배열을 쌓기 위한 `lowestScores` 배열을 만든다.
2. score를 `forEach`로 반복하는데 우선 stack 자료 구조를 통해 처리하기 위해 hallOfFameScores 배열에 현재 score를 `push` 해준다.
3. push 후 현재 hallOfFameScores 배열의 `length`가 `k`를 초과하면 해당 `Math.min` 메소드와 `indexOf` 메소드를 활용하여 최저 점수의 index를 구한 뒤 `splice` 메소드를 통해 제거한다.
4. k의 length를 가지는 hallOfFameScores 배열의 최저 점수를 구하여 일별 최저 점수 배열인 `lowestScores` 변수에 `push` 해준다.
5. 반복문을 종료한 뒤 일별 최저 점수 배열인 `lowestScores` 배열을 출력한다.

<br>
<br>

## **3. 인기 풀이**

```jsx
const othersSolution = (k, score) => {
  const stack = [];

  return score.reduce((a, c) => {
    if (stack.length < k) {
      stack.push(c);
      stack.sort((a, b) => a - b);
    } else {
      stack.push(c);
      stack.sort((a, b) => a - b);
      stack.shift();
    }

    a.push(stack[0]);
    return a;
  }, []);
};

console.log(othersSolution(3, [10, 100, 20, 150, 1, 100, 200])); // [10, 10, 10, 20, 20, 100, 100]
```

1. 현재 배열에 누적해서 쌓기 위해 `reduce` 메소드를 활용하였다. 이 때 기준이 되는 배열은 `score`를 활용하여 내부 점수를 활용할 수 있도록 한다.
2. reduce 내부에서 stack을 쌓기 위한 빈 배열 `stack` 변수에 길이가 `k`를 초과하지 않는 경우 현재 score를 `push`하고 최저 점수를 찾기 위해 `sort` 메소드를 활용하여 오름차순으로 정렬한다.
3. `k`를 초과하는 경우 마찬가지로 현재 score를 `push`하고 최저 점수를 찾기 위해 `sort` 메소드롤 활용하여 오름차순으로 정렬한 뒤 `shift` 메소드를 통해 배열의 맨 앞 요소, 즉 최저 점수를 제거한다.
4. if 조건문에서 stack 변수를 필터링하여 명예의 전당 리스트를 정리한 뒤 해당 `stack의 첫번째 요소`, 즉 현재 `명예의 전당 중 최저 점수`를 reduce 내부 `누적 배열에 push`한 뒤 누적 배열을 return한다.
5. 마지막 요소까지 순회한 뒤 reduce의 결과 값을 출력한다.

<br>
<br>

## **4. 비교**

나의 풀이와 인기 풀이의 경우 가독성은 인기 풀이가 더 좋았던 것 같다. stack을 활용한 풀이 방식은 동일했으나 인기 풀이의 경우 reduce를 활용하여 변수의 생성을 자제하였다. 그리고 reduce 내부에서 조건 등을 통해 결과 값을 출력하는데 동일한 메소드의 활용으로 가독성 또한 좋았던 것 같다. 반면 속도의 경우 테스트 해본 결과 나의 풀이가 조금 더 좋았다.

```jsx
const testArray = Array(30000)
  .fill()
  .map((v, i) => i + 1);
```

위 `testArray`를 생성하여 위 파라미터의 score로 활용하였는데 나의 풀이가 인기 풀이보다 1.2-1.3배, 최대 2배 더 빨랐다. 나의 풀이에서 사용한 `forEach`와 인기 풀이에서 사용한 `reduce`의 시간 복잡도는 `O(n)`으로 동일하다. 하지만 내부 로직 중 아마 최저 점수를 구하는 로직에서 속도 차이가 발생한 것 같다. 내 예상에는 나의 풀이의 경우 최저 점수를 찾을 때 `indexOf`를 활용했는데 인기 풀이의 경우 `sort`를 활용한 것에서 차이가 있었던 것 같다. `indexOf`의 경우 기본적으로 `O(n)`의 시간 복잡도를 가지는데 index를 찾게 되면 즉시 return해서 모든 엘리먼트를 검색하지 않는 것으로 알고 있다. 반면 `sort`의 경우 `O(n log(n))`의 시간 복잡도를 가진다. 두 메소드의 속도를 단순 비교하기는 어렵지만 해당 문제에서는 선형 탐색을 수행하는 indexOf가 조금 더 유리했던 것 같다.

<br>
