# [Algorithm] 프로그래머스 Level 2 - 광물 캐기

2023년 09월 17일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/172927

<br>
<br>

# 2. 나의 풀이

```tsx
// 테스트 케이스 2~7, 10~15, 17~29, 34~35 실패
const mySolution = (picks, minerals) => {
  var answer = 0;

  const fo = {
    diamond: {
      diamond: 1,
      iron: 1,
      stone: 1,
    },
    iron: {
      diamond: 5,
      iron: 1,
      stone: 1,
    },
    stone: {
      diamond: 25,
      iron: 5,
      stone: 1,
    },
  };

  const fd = minerals.map((m) => fo["diamond"][m]);
  const fi = minerals.map((m) => fo["iron"][m]);
  const fs = minerals.map((m) => fo["stone"][m]);

  let i = 0;

  while (i <= minerals.length) {
    const isPicks = Math.max(...picks);

    if (!isPicks) break;

    const sumFd = picks[0] ? fd.slice(i, i + 5).reduce((a, b) => a + b) : 100;
    const sumFi = picks[1] ? fi.slice(i, i + 5).reduce((a, b) => a + b) : 100;
    const sumFs = picks[2] ? fs.slice(i, i + 5).reduce((a, b) => a + b) : 100;
    const minSum = Math.min(sumFd, sumFi, sumFs);

    if (minSum === sumFd) picks[0] -= 1;
    if (minSum === sumFi) picks[1] -= 1;
    if (minSum === sumFs) picks[2] -= 1;

    i += 5;
    answer += minSum;
  }

  return answer;
};

console.log(
  mySolution(
    [1, 3, 2],
    [
      "diamond",
      "diamond",
      "diamond",
      "iron",
      "iron",
      "diamond",
      "iron",
      "stone",
    ]
  )
); // 12
```

1. 각 곡괭이 사용 시 피로도를 담은 객체 fo를 생성하였다.
2. 캐야하는 광물을 배열로 담은 파라미터 minerals를 map 메소드로 돌려 각 곡괭이 별로 현재 광석을 캘 때 소모하는 피로도를 담은 배열 fd, fi, fs 변수를 생성하였다.
3. while 문으로 반복하는데 조건은 i가 minerals의 길이보다 커질 때까지 반복하였다. 이 때 광물은 한 곡괭이 당 5개씩 캘 수 있으므로 i는 5씩 증가되도록 하였다.
4. 반복문 내부에서 첫번째로 Math.max 메소드를 사용하여 현재 사용할 곡괭이가 있는지 확인하였다. 사용할 곡괭이가 없다면 반복문이 종료되도록 하였다.
5. 각 곡괭이로 현재 구간부터 5개의 광물을 캘 때 드는 피로도를 합산하여 sumFd, sumFi, sumFs 변수에 각각 할당하였다. 이 때 해당 곡괭이가 없다면 최저 값에 포함되지 않도록 100이 할당되도록 하였다. 그 후 세 가지 변수 중에 최소 값을 구하기 위해 Math.min을 활용하여 최소 값을 구하였다.
6. 최소 값과 각 곡괭이로 현재 구간부터 5개의 광물을 캘 때 드는 피로도가 같은 경우를 찾아 if 문의 조건으로 활용하였다. 즉 현재 구간을 캘 때 최소 피로도로 캘 수 있는 값을 구하여 해당 곡괭이는 사용하였기 때문에 개수를 감소시키고 최소 값을 answer 변수에 누적하여 더해주었다.
7. 최종 값 answer을 출력한다.

<br>
<br>

# 3. 인기 풀이

```tsx
const othersSolution = (picks, minerals) => {
  const remainPicks = [...picks];
  const maxFatigue = [];
  const useable = minerals.slice(0, picks.reduce((acc, cur) => acc + cur) * 5);

  useable.forEach((mineral, index) => {
    if (index % 5 === 0) maxFatigue.push({ diamond: 0, iron: 0, stone: 0 });
    maxFatigue.at(-1)[mineral]++;
  });

  maxFatigue.sort((a, b) => {
    const aFatigue = a.diamond * 25 + a.iron * 5 + a.stone;
    const bFatigue = b.diamond * 25 + b.iron * 5 + b.stone;

    return bFatigue - aFatigue;
  });

  const answer = maxFatigue.reduce((acc, { diamond, iron, stone }) => {
    if (remainPicks[0] !== 0) {
      remainPicks[0]--;
      return acc + diamond + iron + stone;
    }

    if (remainPicks[1] !== 0) {
      remainPicks[1]--;
      return acc + diamond * 5 + iron + stone;
    }

    remainPicks[2]--;
    return acc + diamond * 25 + iron * 5 + stone;
  }, 0);

  return answer;
};

console.log(
  othersSolution(
    [1, 3, 2],
    [
      "diamond",
      "diamond",
      "diamond",
      "iron",
      "iron",
      "diamond",
      "iron",
      "stone",
    ]
  )
); // 12
```

1. 곡괭이의 개수가 담긴 배열 picks를 복제하여 remainPicks 변수에 할당한다.
2. 캐야하는 광물의 개수를 카운트한 객체를 담기 위한 변수 maxFatigue를 생성한다.
3. 캐야하는 광물이 담긴 배열 minerals를 slice 메소드로 자르는데 이 때 배열의 첫번째 요소부터 최대 캘 수 있는 광물의 개수까지 자른 후 useable 변수에 할당한다.
4. 캘 수 있는 광물을 5개씩 잘라서 객체로 반환하는데 객체의 프로퍼티는 광물의 이름을 key, 광물의 개수를 value로 할당한다. 그리고 해당 객체를 maxFatigue 변수에 push한다.
5. 캐야 하는 광물을 객체로 담은 배열 maxFatigue 변수를 정렬하는데 정렬 기준은 해당 구간의 광물을 캘 때 드는 피로도 순으로 내림차순 정렬한다.
6. 캐야 하는 광물을 객체로 담은 배열 maxFatigue 변수의 요소 값을 합산하는데 reduce 메소드를 활용하여 순회하며 합산한다. reduce 메소드 콜백 내부에서 if 문을 통해 사용할 곡괭이를 지정하는데 사용하는 곡괭이는 다이아몬드 -> 철 -> 돌 곡괭이 순으로 사용한다. 왜냐하면 위에서 maxFatigue 변수에 광물을 캐야하는 구간을 피로도가 높은 순으로 내림차순 정렬하였고 피로도가 높은 광물을 피로도 효율이 좋은 곡괭이부터 사용해야 효율적이기 때문에 효율이 좋은 곡괭이 순으로 사용하는 것이다. 피로도 효율이 좋은 곡괭이부터 해당 곡괭이가 있다면 해당 곡괭이의 개수를 줄이고 해당 곡괭이를 사용하였을 때 드는 피로도를 누적 값에 더해준다.
7. 최종적으로 누적 값을 반환한다.

<br>
<br>

# 4. 비교

우선 해당 문제를 풀며 느낀 점은 너무나 아쉬웠다. 레벨 2의 문제를 풀면서 이건 잘 풀었다라고 느꼈던 적이 아직까지는 없었는데 해당 문제는 잘 풀었다고 느꼈었다. 하지만 코드 실행 단계에서는 통과했으나 테스트 케이스에서 실패해버렸다. 나의 풀이의 경우 캐야하는 광물이 담긴 배열 minerals을 각 곡괭이로 캘 때 드는 피로도로 변환한 뒤 반복문 내부에서 구간 별로 해당 구간의 최저 피로도로 캘 수 있는 곡괭이를 찾는 방식으로 풀이하였고 인기 풀이의 경우 우선 캘 수 있는 구간을 자른 뒤 해당 구간을 피로도가 높은 순으로 정렬하고 피로도 효율이 좋은 곡괭이부터 순차적으로 사용하는 방식으로 풀이하였다. 두 풀이 방식을 비교하며 느낀 점은 비교 글을 작성하면서도 느낄 수 있었다. 나의 풀이의 경우 로직을 설명하기가 조금 복잡하다는 생각이 들었지만 인기 풀이의 경우 로직을 설명하기가 매우 간편했다. 또한 로직의 효율성도 인기 풀이가 훨씬 좋았던 것 같다. 항상 느끼지만 나의 풀이와 인기 풀이를 비교해보면 정말 많은 현타(?)가 오는 것 같다. 막상 인기 풀이를 해석해보면 왜 나는 이렇게 생각하지 못했지라는 생각이 항상 들고는 한다. 이런 느낀점을 바탕으로 앞으로는 문제를 해결하기 전 시간복잡도, 가독성, 예외사항 등을 지금보다 더욱 고려하여 인기 풀이와 같이 깔끔한 코드를 짤 수 있도록 고민을 많이 해야겠다.

<br>
