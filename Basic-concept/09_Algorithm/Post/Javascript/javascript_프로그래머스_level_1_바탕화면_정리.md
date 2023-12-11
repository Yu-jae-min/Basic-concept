# [Algorithm] 프로그래머스 Level 1 - 바탕화면 정리

2023년 09월 07일

<br>

## 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/161990

<br>
<br>

## 2. 나의 풀이

```jsx
const mySolution = (wallpaper) => {
  const dragPositin = {
    lux: null,
    luy: null,
    rdx: null,
    rdy: null,
  };

  for (let i = 0; i < wallpaper.length; i++) {
    const fileFirstIdx = wallpaper[i].indexOf("#");
    const fileLastIdx = wallpaper[i].lastIndexOf("#");
    const { lux, luy, rdx, rdy } = dragPositin;

    if (fileFirstIdx < 0) continue;
    if (lux === null) dragPositin.lux = i;
    if (luy === null || luy > fileFirstIdx) dragPositin.luy = fileFirstIdx;
    if (rdy === null || rdy < fileLastIdx + 1)
      dragPositin.rdy = fileLastIdx + 1;
    dragPositin.rdx = i + 1;
  }

  return [dragPositin.lux, dragPositin.luy, dragPositin.rdx, dragPositin.rdy];
};

console.log(mySolution([".#...", "..#..", "...#."])); // [0, 1, 3, 4]
```

1. 마우스 드래그 포지션 좌표 값을 저장하기 위한 객체 dragPositin을 생성하였다.
2. 바탕화면 내 파일 위치를 문자열로 표시하는 배열 wallpaper를 for문으로 반복하는데 이 때 내부에서는 우선 파일의 위치를 표시하는 문자열 #의 index를 구하였다. 이 때 문자열 안에 파일은 중복으로 존재할 수 있기 때문에 indexOf 메소드로 첫 문자의 index를 구하고 lastIndexOf 메소드로 마지막 문자의 index 모두 구하였다.
3. 조건문을 활용하여 포지션을 할당하는데 첫번째로 파일이 존재하지 않는 경우 다음 사이클로 넘겼다.
4. 두번째 조건으로 좌측 포인트의 x축 위치를 표시하는 lux를 할당하는데 최상단에 위치한 파일을 기준으로 할당해야하므로 첫번째 사이클에서만 해당 값을 할당해준다.
5. 세번째 조건으로 좌측 포인트의 y축 위치를 표시하는 luy를 할당하는데 luy가 비어있거나 기존 luy가 현재 fileFirstIdx보다 큰 경우, 즉 현재 파일의 위치가 기존 파일의 위치보다 더 좌측에 위치한 경우 새로운 값을 할당해준다.
6. 네번째 조건으로 우측 포인트의 y축 위치를 표시하는 rdy를 할당하는데 rdy가 비어있거나 기존 rdy가 현재 fileLastIdx보다 큰 경우, 즉 현재 파일의 위치가 기존 파일의 위치보다 더 우측에 위치한 경우 새로운 값을 할당해준다.
7. 다섯번째 조건으로 우측 포인트 x축 위치를 표시하는 rdx를 할당하는데 최하단에 위치한 파일을 기준으로 할당해야하므로 마지막 사이클까지 해당 값을 할당해준다.
8. 최종적으로 dragPositin 객체의 프로퍼티 value를 배열에 할당하여 반환한다.

<br>
<br>

## 3. 인기 풀이

```jsx
const othersSolution = (wallpaper) => {
  let left = [];
  let top = [];
  let right = [];
  let bottom = [];

  wallpaper.forEach((v, i) => {
    [...v].forEach((val, ind) => {
      if (val === "#") {
        left.push(i); // 0
        top.push(ind); // 1
        right.push(i + 1); // 1
        bottom.push(ind + 1); // 2
      }
    });
  });

  return [
    Math.min(...left),
    Math.min(...top),
    Math.max(...right),
    Math.max(...bottom),
  ];
};

console.log(othersSolution([".#...", "..#..", "...#."])); // [0, 1, 3, 4]
```

1. 좌표 값을 담기 위한 배열 left, top, right, bottom을 생성한다.
2. 파일 위치를 표시한 문자열이 담긴 배열 wallpaper를 forEach로 순회하는데 이 때 내부에서 spread 문법을 통해 각 문자열을 잘라서 배열로 만들어준다.
3. 자른 배열을 다시 forEach로 순회하는데 이 때 좌표 값을 담기 위한 배열 left, top, right, bottom에 현재 위치를 각각 push하여 준다.
4. 최종 값을 출력하기 위해 모든 좌표 값이 더해져있는 left, top, right, bottom 배열을 활용하는데 좌측 포인트의 경우 최소 값을 구해야하므로 Math.min을 사용하고 우측 포인트의 경우 최대 값을 구해야하므로 Math.max를 사용하여 각 배열의 최소 값과 최대 값을 구해 출력한다.

<br>
<br>

## 4. 비교

나의 풀이와 인기 풀이의 경우 풀이 속도 차이는 거의 없었다. 하지만 풀이 방식이 달랐는데 나의 풀이의 경우 조건을 이것저것 붙여서 풀이한 반면 인기 풀이의 경우 #인 경우만 확인하여 그에 대한 위치 값을 모두 구한 뒤 최소 값과 최대 값을 구하는 방식으로 풀이하였다. 누가봐도 가독성, 풀이 방식 모두 인기 풀이의 방법이 좋았던 것 같다. 시간 복잡도가 증가하는 것을 피하기 위해 중첩 반복문의 사용을 지양했었는데 indexOf와 lastIndexOf의 사용으로 인해 중첩 반복문을 사용한 인기 풀이와 속도도 큰 차이가 없었다. 나의 풀이와 인기 풀이를 비교해보며 느낀 점은 로직을 작성할 때 조건 하나한 생각해가며 그때 그때 조건을 추가하는 것보다 결과를 우선적으로 생각해보는 것이 중요하다고 느꼈다. 인기 풀이의 경우 최소 값과 최대 값을 구해야한다는 결과를 생각했기 때문에 심플하게 모든 값을 배열로 담은 뒤 최소 값과 최대 값을 비교하는 방식으로 풀 수 있었던 것 같다.

<br>
