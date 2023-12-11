# [Algorithm] 프로그래머스 Level 1 - 공원 산책

2023년 09월 09일

<br>

## 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/172928

<br>
<br>

## 2. 나의 풀이

```jsx
const mySolution = (park, routes) => {
  const answer = [0, 0]; // 초기 좌표 설정, [세로 좌표, 가로 좌표]
  const parkMap = park.map((parkItem) => [...parkItem]); // 내부 문자를 배열로 변경
  const parkWidth = parkMap[0].length; // 공원의 최대 가로 길이
  const parkHeight = parkMap.length; // 공원의 최대 세로 길이

  // "S"의 경우 시작 지점이므로 시작 지점 좌표 구하기
  for (let i = 0; i < parkHeight; i++) {
    if (!parkMap[i].includes("S")) continue;

    answer[0] = i;
    answer[1] = parkMap[i].indexOf("S");
    break;
  }

  // 이동 좌표가 담긴 배열 "routes"를 활용하여 반복문 실행
  for (let i = 0; i < routes.length; i++) {
    const [dir, str] = routes[i].split(" "); // 구조 분해를 통한 좌표방향 "dir"과 이동거리 "str" 분해
    const val = Number(str); // string 타입의 거리를 number 타입으로 변경

    const vp = answer[0]; // 현재 세로 좌표 값
    const hp = answer[1]; // 현재 가로 좌표 값

    // 방향 체크 변수 생성
    const isEast = dir === "E";
    const isWest = dir === "W";
    const isSouth = dir === "S";
    const isNorth = dir === "N";

    // 이동해야 하는 방향이 동쪽이나 서쪽인 경우
    if (isEast || isWest) {
      const nhp = isEast ? hp + val : hp - val; // 이동 방향이 동쪽인 경우 현재 가로 좌표에 이동 거리를 더하고 서쪽인 경우 현재 가로 좌표에 이동 거리를 빼 다음 좌표 구하기
      const isOver = isEast ? nhp >= parkWidth : nhp < 0; // 이동 방향이 동쪽인 경우 이동할 좌표가 공원에 크기보다 크거나 같음을 확인하고 서쪽인 경우 공원에 가장 좌측 위치인 0보다 작은지 확인

      if (isOver) continue; // 공원을 벗어나기 때문에 다음 사이클로 넘김

      // 공원의 현재 세로 좌표에 해당하는 배열을 slice로 자르는데 이동 방향이 동쪽인 경우 기존 위치부터 다음 위치까지 자르고 서쪽인 경우 다음 위치부터 기존 위치까지 자름
      const mpi = isEast
        ? parkMap[vp].slice(hp, nhp + 1)
        : parkMap[vp].slice(nhp, hp + 1);
      const isObstacles = mpi.includes("X"); // 이동 경로 요소가 담긴 배열에 장애물이 포함되어 있는지 확인

      if (isObstacles) continue; // 장애물이 있기 때문에 다음 사이클로 넘김

      answer[1] = nhp; // 가로 좌표 갱신
    }

    // 이동해야 하는 방향이 남쪽이나 북쪽인 경우
    if (isSouth || isNorth) {
      const nvp = isSouth ? vp + val : vp - val; // 이동 방향이 남쪽인 경우 현재 세로 좌표에 이동 거리를 더하고 북쪽인 경우 현재 세로 좌표에 이동 거리를 빼 다음 좌표 구하기
      const isOver = isSouth ? nvp >= parkHeight : nvp < 0; // 이동 방향이 남쪽인 경우 이동할 좌표가 공원에 크기보다 크거나 같음을 확인하고 북쪽인 경우 공원에 가장 상단 위치인 0보다 작은지 확인

      if (isOver) continue; // 공원을 벗어나기 때문에 다음 사이클로 넘김

      // 공원 배열을 slice로 자르는데 이동 방향이 남쪽인 경우 기존 위치부터 다음 위치까지 자르고 북쪽인 경우 다음 위치부터 기존 위치까지 자른 후 각 배열에서 현재 가로 좌표에 해당하는 요소들만 뽑아냄
      const mpi = isSouth
        ? parkMap.slice(vp, nvp + 1).map((item) => item[hp])
        : parkMap.slice(nvp, vp + 1).map((item) => item[hp]);
      const isObstacles = mpi.includes("X"); // 이동 경로 요소가 담긴 배열에 장애물이 포함되어 있는지 확인

      if (isObstacles) continue; // 장애물이 있기 때문에 다음 사이클로 넘김

      answer[0] = nvp; // 세로 좌표 갱신
    }
  }

  return answer; // 최종 좌표 출력
};

console.log(mySolution(["SOO", "OOO", "OOO"], ["E 2", "S 2", "W 1"])); // [2, 1]
```

주석 참고

<br>
<br>

## 3. 인기 풀이

```jsx
const othersSolution = (park, routes) => {
  const dirs = { E: [0, 1], W: [0, -1], S: [1, 0], N: [-1, 0] }; // 각 좌표를 객체 key로 활용하여 이동 좌표를 배열로 할당
  let [x, y] = [0, 0]; // 현재 좌표 생성

  // "S"의 경우 시작 지점이므로 시작 지점 좌표 구하기
  for (let i = 0; i < park.length; i++) {
    if (park[i].includes("S")) {
      [x, y] = [i, park[i].indexOf("S")];
      break;
    }
  }

  // 이동 좌표가 담긴 배열 "routes"를 활용하여 반복문 실행
  routes.forEach((route) => {
    const [r, n] = route.split(" "); // 구조 분해를 통한 좌표방향 "r"과 이동거리 "n" 분해

    let [nx, ny] = [x, y]; // 이전 좌표 값 할당
    let cnt = 0; // 전진한 칸 수, 칸을 이동할 때마다 1씩 증가

    // 이동 좌표까지 한칸 씩 전진하기 위해 while문 활용, 이동 칸수가 이동할 칸수보다 작은 경우만 실행
    while (cnt < n) {
      [nx, ny] = [nx + dirs[r][0], ny + dirs[r][1]]; // 현재 좌표에서 이동할 방향만큼 한칸 이동

      // park[nx]를 통해 공원을 세로로 벗어나거나, park[nx][ny]를 통해 공원을 가로로 벗어나거나, park[nx][ny] === "X"를 통해 다음 이동할 칸에 장애물이 있는지 확인 후 하나라도 해당된다면 while 반복문을 중단시킴
      if (!park[nx] || !park[nx][ny] || park[nx][ny] === "X") break;
      cnt++;
    }

    // while문에서 break가 걸리지 않아 이동할 칸수만큼 모두 전진했다면 좌표 값을 갱신하기 위해 이동이 완료된 좌표 값을 x, y에 할당하고 break가 걸려 이동할 칸수만큼 모두 전진하지 못했다면 할당하지 않고 다음 사이클로 넘어감
    if (cnt == n) [x, y] = [nx, ny];
  });

  return [x, y]; // 최종 좌표 출력
};

console.log(othersSolution(["SOO", "OOO", "OOO"], ["E 2", "S 2", "W 1"])); // [2, 1]
```

주석 참고

<br>
<br>

## 4. 비교

나의 풀이와 인기 풀이의 경우 우선 속도는 거의 비슷했다. 하지만 코드 길이가 매우 많이 차이 나는 것을 볼 수 있다. 여기서 가독성 차이가 발생한 것 같다. 우선 나의 풀이의 경우 동서와 남북을 구분하여 작업하였으나 인기 풀이의 경우 한번에 처리하였다. 나의 경우 동서와 남북을 나눈 이유는 가로 방향과 세로 방향 이동에 있어 처리해야 할 로직들이 구분되어야 한다고 생각하였다. 예를 들면 동서의 경우 가로 방향으로 공원을 벗어나는 지 확인했고 남북의 경우 세로 방향으로 공원을 벗어나는 지 확인했다. 또한 장애물의 경우 이동할 위치에 배열 요소들을 모두 구한 뒤에 해당 요소들 중 장애물을 나타내는 “X”가 포함되는지 확인하는 방식으로 장애물을 확인하였다. 하지만 인기 풀이의 경우 동서남북을 구분하지 않고 이동할 좌표 객체를 우선 생성해놓은 뒤 반복문 내부에 while문을 활용하여 한칸 씩 전진하도록 했다. 문제에서 제시하고 있는 풀이 의도를 잘 이해한 것 같았다. while문을 통해 한칸 씩 전진해나가며 현재 위치가 공원을 벗어나거나 함정이 있다면 while문을 멈추고 다음 사이클로 자연스럽게 넘어가도록 하였다. 나와 같이 동서남북을 구분하여 작업한 것보다 한번에 처리하니 훨씬 간결해보이고 깔끔했다.

나의 풀이와 인기 풀이를 비교해보며 느낀점은 문제를 풀이하기 전 다양하고 사고하는 것이 중요하다고 생각이 들었다. 나는 최종 위치를 우선 구한 뒤 그 최종 위치로 가는 요소들을 모조리 구해 장애물을 파악하였는데 이 방법말고 인기 풀이와 같이 한칸 씩 전진해나가며 현재 위치에 문제가 없는지 확인한 후 다음 칸으로 전진하도록 하였는데 조금 더 고민했다면 충분히 생각해낼 수 있는 방법이었다고 생각한다. 알고리즘 문제를 풀며 항상 느끼는 점이지만 무작정 코드를 작성하기보다 충분한 시간을 가지고 고민한 후 작성하는 것이 훨씬 효율적이라는 생각이 든다. 앞으로는 더 생각하고 작업하는 습관을 길러야겠다.

<br>
