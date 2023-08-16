# **[Algorithm] 프로그래머스 Level 1 - 성격 유형 검사**

2023년 08월 17일

<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/118666

<br>
<br>

## **2. 나의 풀이**

```tsx
const mySolution = (survey, choices) => {
  const score = [
    {
      R: 0,
      T: 0,
    },
    {
      C: 0,
      F: 0,
    },
    {
      J: 0,
      M: 0,
    },
    {
      A: 0,
      N: 0,
    },
  ];

  survey.forEach((surveyItem, index) => {
    return score.forEach((scoreItem, idx) => {
      const firstKey = Object.keys(scoreItem)[0];
      const includeKey = surveyItem.includes(firstKey);
      const IncrementKey = choices[index] < 4 ? surveyItem[0] : surveyItem[1];
      const IncrementScore = Math.abs(choices[index] - 4);

      if (!includeKey) return;

      return (score[idx][IncrementKey] += IncrementScore);
    });
  });

  const answer = score
    .map((scoreItem) => {
      const firstKey = Object.keys(scoreItem)[0];
      const firstValue = Object.values(scoreItem)[0];
      const secondKey = Object.keys(scoreItem)[1];
      const secondValue = Object.values(scoreItem)[1];

      return firstValue < secondValue ? secondKey : firstKey;
    })
    .join("");

  return answer;
};

console.log(mySolution(["AN", "CF", "MJ", "RT", "NA"], [5, 3, 2, 7, 5])); // "TCMA"
```

1. 반복문을 중첩해서 사용하였다. 이 때 첫번째 반복문은 파라미터로 전달받은 성격 유형 지표 `survey`를 기준으로 반복하였다.
2. 두번째 내부 반복문에서는 점수를 기록하기 위해 생성한 배열 `score`를 기준으로 반복하였다. 이 때 첫번째 반복문이 돌고 있는 문자열에 현재 스코어의 `key`가 포함되어 있는지 확인하여 증가시킬 key group을 찾았다.
3. 변수 `IncrementKey`에 만약 key가 포함되어 있다면 7점 사이에 기준 점수 4점을 초과하지 않는 경우 첫번째 key, 초과하는 경우 두번째 key 값을 증가시켰다. 예를 들어 “AN”을 기준으로 4점을 초과하지 않는 경우는 “A”, 초과하지 않는 경우는 “N”을 할당하도록 하였다.
4. 증가시키는 점수는 1~3점인 경우 성격 유형 지표 문자의 좌측 유형 1~3점 증가, 5~7점인 경우 우측 유형을 1~3점 증가, 4점인 경우 증가시키지 않기 때문에 `IncrementScore` 변수에 `-4`를 빼준 뒤 절대 값으로 변경하였다.
5. 중첩 반복문 내부에서 최종적으로 증가시킬 키의 그룹 `score[idx]`, 증가시킬 키 `IncrementKey`, 증가시킬 점수 `IncrementScore` 를 활용하여 스코어를 증가시켰다.
6. 스코어를 증가시키고 난 후 map 메소드를 활용하여 key group마다 큰 key의 value를 반환하도록 하였다. 이 때 같은 점수인 경우 알파벳 순서로 반환해야하므로 처음 생성할 때 알파벳 순으로 key를 만들어놓았다.

<br>
<br>

## **3. 인기 풀이**

```tsx
const othersSolution = (survey, choices) => {
  const MBTI = {};
  const types = ["RT", "CF", "JM", "AN"];

  types.forEach((type) => type.split("").forEach((char) => (MBTI[char] = 0)));

  choices.forEach((choice, index) => {
    const [disagree, agree] = survey[index];

    MBTI[choice > 4 ? agree : disagree] += Math.abs(choice - 4);
  });

  return types.map(([a, b]) => (MBTI[b] > MBTI[a] ? b : a)).join("");
};

console.log(othersSolution(["AN", "CF", "MJ", "RT", "NA"], [5, 3, 2, 7, 5])); // "TCMA"
```

1. 스코어를 증가시키기 위한 변수 `MBTI`의 빈 객체를 할당하고 성격 유형 종류가 묶인 배열 `types`를 생성한 뒤 types 배열을 반복문으로 돌려 배열 요소를 쪼개어 가공한 뒤 MBTI 변수에 스코어를 할당할 수 있도록 객체 key, value를 생성하였다.
2. 스코어를 증가시키기 위한 객체를 만든 뒤 스코어를 채우기 위해 다시 반복문을 활용하였다. 반복문을 돌릴 때 기준이 되는 배열은 파라미터로 전달받은 점수 목록 `choices`가 되었고 반복문 내부에서 함수 내부로 전달받은 검사할 성격 유형 종류가 묶인 배열 `survey`를 `disagree`, `agree`로 구조분해 하였다. 그 후 기준 점수 4점을 넘는지 안넘는지를 비교하여 MBTI 객체에 증가시킬 key를 찾았고 증가시킬 점수는 반복되는 점수 배열에서 현재 배열 요소 점수 중 4점을 뺸 뒤 정수로 변환하여 증가시킬 점수를 구하였다.
3. 최종적으로 누산 된 점수를 출력하기 위해 types 배열을 돌리는데 이 때 해당 배열 요소를 구조분해 한 뒤 해당 배열 요소들을 key로 사용하여 MBTI 내부에 value를 비교하여 큰 key를 반환하도록 하였다. 그리고 최종적으로 join하여 문자열로 변경되도록 하였다.

<br>
<br>

## **4. 비교**

나의 풀이와 인기 풀이를 비교해보았을 때 인기 풀이가 압도적으로 좋았던 것 같다. 일단 풀어가는 방식 자체는 비슷했다. 카운트를 증가시킬 객체를 생성하고, 카운트를 증가시키고, 증가시킨 카운트의 key를 비교하여 큰 key를 반환하고, 최종적으로 합쳐 문자열로 반환하였다. 하지만 구현 방식은 모두 달랐다. 일단 객체를 생성하는 방법부터 인기 풀이의 경우 배열을 생성한 뒤 가공하는 방식을 활용하여 코드의 길이를 줄였다. 또한 반환할 때도 해당 배열을 활용하여 key group을 묶어 비교할 수 있도록 사용하였다. 또한 증가시키는 방법도 달랐다. 반복문을 사용한 것은 동일하지만 인기 풀이의 경우 구조 분해와 변수명을 통해 매우 명확하게 MBTI 객체의 value를 증가시키도록 하였다. 그리고 마지막 출력 부분에서도 나의 풀이의 경우 객체를 문자열로 가공하기 위한 코드가 많이 포함되어 있었지만 인기 풀이의 경우 스코어를 높이기 위해 사용한 types 배열을 사용하였고 내부에서 또 다시 구조분해를 통해 간결하게 비교하였다. 나의 풀이와 인기 풀이를 비교해보며 느낀 점은 구조 분해는 나도 평소에 사용하던 스킬이었고 모르는 스킬이 아니었음에도 사용하는 것을 떠올리지 못했다. 하지만 인기 풀이의 경우 구조 분해를 사용하여 코드를 간결하게 사용하여 가독성을 좋게한 부분이 너무 좋은 코드인 것 같다. 평소 아는 것들을 적극적으로 활용해보는 습관도 필요한 것 같다.

<br>
