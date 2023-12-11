# **[Algorithm] 프로그래머스 Level 1 - 로또의 최고 순위와 최저 순위**

2023년 08월 09일

<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/77484

<br>
<br>

## **2. 나의 풀이**

```tsx
const mySolution = (lottos, win_nums) => {
  var answer = [];

  const maxCount = lottos.filter(
    (num) => num === 0 || win_nums.includes(num)
  ).length;
  const minCount = lottos.filter((num) => win_nums.includes(num)).length;
  const countArr = [maxCount, minCount];

  countArr.forEach((el) => {
    if (el === 6) return answer.push(1);
    if (el === 5) return answer.push(2);
    if (el === 4) return answer.push(3);
    if (el === 3) return answer.push(4);
    if (el === 2) return answer.push(5);
    else return answer.push(6);
  });

  return answer;
};

console.log(mySolution([44, 1, 0, 0, 31, 25], [31, 10, 45, 1, 6, 19])); // [3, 5]
```

1. 로또의 최고 순위를 구하기 위해 `maxCount` 변수에 찍은 번호를 필터하여 할당하였다. 이 때 필터 조건은 해당 번호가 0 이거나 당첨 번호에 포함되어 있는 경우로 지정하였다. 결과로 나온 배열의 length를 할당하여 당첨 된 번호의 최고 수를 구하였다.
2. 로또의 최저 순위를 구하기 위해 `minCount` 변수에 찍은 번호를 필터하여 할당하였다. 이 때 필터 조건은 해당 번호가 당첨 번호에 포함되어 있는 경우로 지정하였다. 결과로 나온 배열의 length를 할당하여 당첨 된 번호의 최저 수를 구하였다.
3. 최저 수와 최고 수를 활용하여 등수를 구하였다. forEach로 반복문을 돌리는데 최저 수 혹은 최고 수에 따라서 등수를 부여하여 `answer` 변수에 push 하였다.

<br>
<br>

## **3. 인기 풀이**

```tsx
const othersSolution = (lottos, win_nums) => {
  const rank = [6, 6, 5, 4, 3, 2, 1];

  let minCount = lottos.filter((v) => win_nums.includes(v)).length;
  let zeroCount = lottos.filter((v) => !v).length;

  const maxCount = minCount + zeroCount;

  return [rank[maxCount], rank[minCount]];
};

console.log(othersSolution([44, 1, 0, 0, 31, 25], [31, 10, 45, 1, 6, 19])); // [3, 5]
```

1. `rank` 변수를 만들어 등수를 할당하였다.
2. 로또의 최저 순위를 구하기 위해 `minCount` 변수에 찍은 번호를 필터하여 할당하였다. 이 때 필터 조건은 해당 번호가 당첨 번호에 포함되어 있는 경우로 지정하였다. 결과로 나온 배열의 length를 할당하여 당첨 된 번호의 최저 수를 구하였다.
3. 로또의 최고 순위를 구하기 위해 `zeroCount` 변수에 찍은 번호를 필터하여 할당하였다. 이 때 필터 조건은 해당 번호가 true인 경우로 지정하였는데 0은 false로 취급되므로 ! 연산자를 활용하여 true인 경우를 지정하였다. 결과로 나온 배열의 length를 할당하여 당첨 된 번호의 최고 수를 구하였다.
4. 등수를 출력하기 위해 rank 변수에 최고 수와 최저 수를 index로 활용하여 출력하였다.

나의 풀이와 인기 풀이의 큰 차이점은 추가적인 반복문이 없다는 것이다. 최저 수와 최고 수를 구하는 로직은 비슷했지만 여기서 차이가 발생했다. 인기 풀이의 경우 `rank` 라는 변수를 만들어 등수를 할당하고 최저 수와 최고 수를 index로 활용하여 추가적인 로직을 사용하지 않았다. 등수 6부터 1까지 규칙적으로 증가한다는 점을 활용한 좋은 방법인 것 같다.

<br>
