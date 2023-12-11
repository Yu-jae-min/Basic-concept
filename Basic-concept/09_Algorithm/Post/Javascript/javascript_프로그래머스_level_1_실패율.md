# **[Algorithm] 프로그래머스 Level 1 - 실패율**

2023년 07월 28일

<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/42889

<br>
<br>

## **2. 나의 풀이**

```tsx
const mySolution = (N, stages) => {
  const baseArr = Array(N)
    .fill("")
    .map((_, index) => [String(index + 1), 0]);
  const countObj = Object.fromEntries(baseArr);

  baseArr.forEach(([key, _]) => {
    const count = stages.reduce((cur, el) => cur + (Number(key) === el), 0);
    const len = stages.filter((el) => el >= key).length;
    countObj[key] = count / len;
  });

  const sortArr = Object.entries(countObj)
    .sort((a, b) => b[1] - a[1])
    .map(([key, _]) => Number(key));

  return sortArr;
};

console.log(mySolution(5, [2, 1, 2, 6, 2, 4, 3, 3])); // [3, 4, 2, 1, 5]
```

1. 기준 배열을 만들고 해당 배열을 객체로 변환하였다.
2. `forEach`로 기준 배열 길이만큼 반복하였다.
3. 반복문 내부에서 `reduce` 메서드를 활용하여 플레이어가 도달한 스테이지가 현재 스테이지와 같은 경우, 즉 현재 스테이지에 도달하였으나 클리어하지 못한 플레이어 수를 구하여 `count` 변수에 담았다.
4. 반복문 내부에서 `len` 메서드를 활용하여 플레이어가 도달한 스테이지가 현재 스테이지와 같거나 큰 경우, 즉 스테이지에 도달한 플레이어 수를 구하여 `len` 변수에 담았다.
5. 실패율 순으로 스테이지를 정렬하기 위해 `sort` 메서드를 활용하였다. 그 후 해당 배열의 key만을 출력하기 위해 `map` 을 활용하였다.

<br>
<br>

## **3. 인기 풀이**

```tsx
const othersSolution = (N, stages) => {
  let result = [];

  for (let i = 1; i <= N; i++) {
    let reach = stages.filter((x) => x >= i).length;
    let curr = stages.filter((x) => x === i).length;
    result.push([i, curr / reach]);
  }

  result.sort((a, b) => b[1] - a[1]);

  return result.map((x) => x[0]);
};

console.log(othersSolution(5, [2, 1, 2, 6, 2, 4, 3, 3])); // [3, 4, 2, 1, 5]
```

1. `for`문을 통해 반복하였는데 이 때 스테이지는 1부터 시작이므로 초기 값은 1로 설정하였고 스테이지 갯수와 같거나 작은 경우만 반복되도록 하였다.
2. 반복문 내부에서 `filter` 메서드를 활용하여 플레이어가 도달한 스테이지가 현재 스테이지와 같은 경우, 즉 현재 스테이지에 도달하였으나 클리어하지 못한 플레이어 수를 구하여 `curr` 변수에 담았다.
3. 반복문 내부에서 `filter` 메서드를 활용하여 플레이어가 도달한 스테이지가 현재 스테이지와 같거나 큰 경우, 즉 스테이지에 도달한 플레이어 수를 구하여 `reach` 변수에 담았다.
4. 위 두 변수를 활용하여 실패율을 구한 뒤 스테이지 값과 함께 `result` 변수에 `push` 하였다.
5. 실패율 순으로 스테이지를 정렬하기 위해 `sort` 메서드를 활용하였다. 그 후 해당 배열의 key만을 출력하기 위해 `map`을 활용하였다.

나의 풀이와 비교했을 때 문제를 해결하는 방식에는 크게 차이가 없었다. 하지만 코드를 보면 알 수 있듯이 나의 코드는 매우 복잡해보인다. 이유는 형 변환이 추가되었기 때문이다. 나의 풀이는 배열에서 객체로 형 변환을 한 뒤 다시 배열로 형 변환을 하여 추가되는 코드가 많았다. 반면 인기 풀이의 경우 처음 함수 내부로 전달받은 파라미터를 그대로 활용하여 깔끔하게 구현이 되었다. 또 메서드를 통일해서 사용하여 더욱 깔끔해보이도록 하였다. 비교해보며 느낀점은 쓸데없는 형 변환은 하지말아야겠다고 느꼈다.
