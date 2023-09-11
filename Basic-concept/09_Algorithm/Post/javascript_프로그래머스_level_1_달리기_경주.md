# [Algorithm] 프로그래머스 Level 1 - 달리기 경주

2023년 09월 11일

<br>

## 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/178871

<br>
<br>

## 2. 나의 풀이

```tsx
// 풀이 1 : 시간 초과
const mySolution1 = (players, callings) => {
  callings.forEach((name) => {
    const idx = players.indexOf(name);
    players.splice(idx, 1);
    players.splice(idx - 1, 0, name);
  });

  return players;
};

// 풀이 2 : 시간 초과
const mySolution2 = (players, callings) => {
  callings.forEach((name) => {
    const idx = players.indexOf(name);

    players[idx] = players[idx - 1];
    players[idx - 1] = name;
  });

  return players;
};

// 풀이 3 : 시간 초과
const mySolution3 = (players, callings) => {
  const rank = {};

  players.forEach((p, i) => (rank[p] = i));

  callings.forEach((c) => {
    const op = rank[c];
    const bop = players[op - 1];

    rank[c] -= 1;
    rank[bop] += 1;

    players[rank[c]] = c;
    players[rank[bop]] = bop;
  });

  return players;
};

console.log(
  mySolution3(
    ["mumu", "soe", "poe", "kai", "mine"],
    ["kai", "kai", "mine", "mine"]
  )
); // ["mumu", "kai", "mine", "soe", "poe"]
```

1. 첫번째 풀이 `mySolution1`의 경우 불리는 선수 이름이 배열로 담긴 callings를 forEach로 순회하는데 현재 rank가 담긴 배열 players 내부에서 현재 불리고 있는 선수의 index를 구한 뒤 해당 index와 splice 메소드를 활용하여 추월한 플레이어를 새로 추가하고 중복되는 기존 플레이어 이름을 제거하였다. 결과는 시간 초과!
2. 두번째 풀이 `mySolution2`의 경우 불리는 선수 이름이 배열로 담긴 callings를 forEach로 순회하는데 현재 rank가 담긴 배열 players 내부에서 현재 불리고 있는 선수의 index를 구한 뒤 해당 index 위치에 추월 당한 플레이어를 할당하고 해당 index에 1을 뺀 위치에 추월한 플레이어를 할당했다. 즉 첫번째 풀이에서 splice 메소드를 제거했다. 결과는 시간 초과!
3. 세번째 풀이 `mySolution3`의 경우 우선 player 배열을 forEach로 순회하여 선수들의 이름과 현재 랭크를 key, value로 저장하였다. 그 후 불리는 선수 이름이 배열로 담긴 callings를 forEach로 순회하는데 op 변수에 추월하는 선수의 기존 점수를 할당하고 bop에 추월당한 선수의 이름을 할당했다. 그 후 현재 랭크를 최신화하기 위해 현재 랭크가 담긴 객체 rank 내부 현재 추월한 선수의 이름을 key로 갖는 프로퍼티의 value를 기존 추월한 선수 점수에 1을 뺀 점수를 할당하였고 추월당한 선수의 이름을 key로 갖는 프로퍼티의 value를 기존 추월한 선수 점수에 1을 더한 점수를 할당하였다. 그 후 player 배열의 순서를 바꿔주는데 추월한 선수의 현재 index에 추월한 선수 이름을 할당하고 추월당한 선수의 현재 index에 추월당한 선수 이름을 할당했다. 결과는 통과!

<br>
<br>

## 3. 인기 풀이

```tsx
const othersSolution = (players, callings) => {
  let idx;
  let name1;
  let name2;
  const idxList = {};

  players.forEach((name, index) => (idxList[name] = index));

  for (let call of callings) {
    idx = idxList[call];
    name1 = players[idx];
    name2 = players[idx - 1];
    idxList[call] -= 1;
    idxList[name2] += 1;
    players[idx] = name2;
    players[idx - 1] = name1;
  }

  return players;
};

console.log(
  othersSolution(
    ["mumu", "soe", "poe", "kai", "mine"],
    ["kai", "kai", "mine", "mine"]
  )
); // ["mumu", "kai", "mine", "soe", "poe"]
```

나의 풀이 3번과 동일하다.

<br>
<br>

## 4. 비교

이번 문제는 시간 초과가 해결이 되지 않아 코멘트를 참고하여 풀었다. 나의 풀이 중 1번이나 2번의 경우 시간 초과가 발생하였다. 코드가 길지 않으니 시간 초과의 원인은 금세 알 수 있었다. 하지만 indexOf를 제외하고는 풀 수 있는 방법이 딱히 떠오르지 않아 splice를 제거하는 방식으로 리팩토링하여 테스트해보았지만 여전히 시간 초과가 발생하였다. 왜냐하면 반복문 내부에서 indexOf를 사용하였기 때문에 시간 복잡도가 여전히 O(nm)을 나타내고 있기 때문이다. 해당 문제의 조건 중 players의 최대치는 50,000 callings의 최대치는 1,000,000 이기 때문에 최악의 경우 50,000 \* 1,000,000 = 50,000,000,000(500억)번 정도 돌아가게 되어 시간 초과가 발생하는 것이다. 프로그래머스 문제의 허용되는 반복 횟수의 경우 백만~천만번까지는 안정권이라고 보고 간혹 일억번까지 허용하는 경우가 있다고 한다. 내 코드의 경우 500배나 초과하는 로직이었다. 그렇기 때문에 indexOf를 제거하는 방법이 필요했다. 그래서 코멘트를 찾아보니 다수의 해시 변수를 사용하여 O(n+m)으로 풀어낼 수 있다고 한다. 해당 코멘트를 참고하여 현재 점수를 나타내는 랭크 변수를 생성하고 해당 변수를 활용하여 풀어내었다.

이번 문제를 풀어보며 느낀 점은 이전 알고리즘 문제를 풀 때는 이 문제를 해결하는 데에 집중했었다. 왜냐하면 난이도가 낮은 알고리즘 문제여서 그런지 해결만 한다면 시간초과가 발생하는 경우는 드물었다. 하지만 이번 케이스와 같이 어떤 기능을 구현하는데 결과 자체는 단순하게 도출해낼 수 있지만 만약 규모가 큰 서비스에서 동작해야하는 로직일 경우도 고려해야한다고 느꼈다. 위와 같이 최대치가 5만에서 100만까지 허용하는 경우 간단한 로직이라도 시간복잡도를 고려하지 않으면 심각하게 차이가 발생할 수 있다. 그렇기 때문에 로직을 짜기전 해결은 당연한 일이며 시간복잡도를 고려해 최대한 시간복잡도가 낮은 연산 비용이 저렴한 로직을 구상한 후 짤 수 있도록 해야겠다. 그러기 위해서는 시간복잡도와 자료구조에 대해 더 학습해야겠다고 느꼈다.

<br>
