# [Algorithm] 프로그래머스 Level 1 - 추억 점수

2023년 09월 10일

<br>

## 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/176963

<br>
<br>

## 2. 나의 풀이

```jsx
const mySolution = (name, yearning, photo) => {
  var answer = [];
  const score = {};

  name.forEach((nameItem, idx) => (score[nameItem] = Number(yearning[idx])));

  photo.forEach((photoItem, idx) => {
    answer[idx] = photoItem
      .map((photoItem) => score[photoItem] || 0)
      .reduce((acc, cur) => acc + cur);
  });

  return answer;
};

console.log(
  mySolution(
    ["may", "kein", "kain", "radi"],
    [5, 10, 1, 3],
    [
      ["may", "kein", "kain", "radi"],
      ["may", "kein", "brin", "deny"],
      ["kon", "kain", "may", "coni"],
    ]
  )
); // [19, 15, 6]
```

1. 스코어를 저장할 객체 score 생성
2. 이름이 담긴 name 파라미터를 forEach 메소드로 반복하는데 name 배열 요소를 score 객체의 내부 key, 점수가 담긴 yearning 배열 요소를 number 타입으로 바꾼 뒤 score 객체의 내부 value로 할당한다.
3. 사진 목록을 2차원 배열로 담아놓은 배열 photo를 forEach 메소드로 순회하는데 우선 내부 배열 요소를 map 메소드로 순회하는데 score 객체를 활용하여 점수로 전환하고 key가 없는 경우 0으로 전환한다.
4. map 메소드를 활용하여 점수로 바뀐 배열을 reduce 메소드를 활용하여 누적해서 더하고 answer 배열 내부 현재 index에 할당해준다.
5. 최종 스코어를 출력한다.

<br>
<br>

## 3. 인기 풀이

```jsx
const othersSolution = (name, yearning, photo) => {
  return photo.map((v) =>
    v.reduce((a, c) => (a += yearning[name.indexOf(c)] ?? 0), 0)
  );
};

console.log(
  othersSolution(
    ["may", "kein", "kain", "radi"],
    [5, 10, 1, 3],
    [
      ["may", "kein", "kain", "radi"],
      ["may", "kein", "brin", "deny"],
      ["kon", "kain", "may", "coni"],
    ]
  )
); // [19, 15, 6]
```

1. 사진 목록을 2차원 배열로 담아놓은 배열 photo를 map 메소드로 순회하는데 내부 배열 요소를 reduce를 통해 합쳐준다. 이 때 초기 값은 0이고 스코어가 배열로 담긴 파라미터 yearning의 요소를 더해주는데 해당 요소의 index는 indexOf 메소드를 활용하여 구해주는데 현재 순회 중인 배열 요소 내부 이름을 활용하여 index를 구한다. 그 후 해당 요소가 존재하면 해당 스코어를 더하고 아닌 경우 0을 더해준다.

<br>
<br>

## 4. 비교

나의 풀이와 인기 풀이를 비교했을 때 속도는 인기 풀이가 더 빨랐다. 또한 코드 길이, 가독성 등도 인기 풀이가 더 좋았던 것 같다. 나의 경우 스코어를 담은 객체를 우선 구한 뒤 사진 목록을 map으로 돌려 스코어를 담은 객체의 key를 찾아 스코어를 누적해서 더했다. 하지만 인기 풀이의 경우 map과 reduce를 통해 바로 더해주었는데 이 때 이름의 담긴 배열 name의 index를 구하여 점수가 담긴 yearning 배열 index로 활용하였다. 즉 index가 같다는 점을 이용해서 코드 길이를 확 줄였다. 두 풀이의 큰 그림 자체는 비슷하였지만 구현하는 방식에서 나의 풀이의 경우 필요없는 과정들이 추가된 것 같다.

<br>
