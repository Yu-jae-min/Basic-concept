# [Algorithm] 프로그래머스 Level 2 - 미로 탈출

2023년 09월 26일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/159993

<br>
<br>

# 2. 나의 풀이

```tsx
// 특정 타겟에 좌표를 가져오는 함수
const getPosition = (key, maps) => {
  for (let i = 0; i < maps.length; i++) {
    if (!maps[i].includes(key)) continue; // 타겟을 포함하고 있지 않다면 다음 사이클로 이동

    const y = i;
    const x = maps[i].indexOf(key);

    return [y, x]; // 타겟을 포함하고 있다면 타겟에 좌표를 반환
  }
};

// BFS(너비 우선 탐색) 함수
const bfs = (target, start, maps) => {
  let count = 0; // 한 칸 이동할 때마다 누적하여 증가시킬 변수 생성
  const moveY = [-1, 1, 0, 0]; // 상, 하 이동 좌표
  const moveX = [0, 0, -1, 1]; // 좌, 우 이동 좌표
  const queue = [start]; // 현재 이동 좌표가 담긴 배열을 쌓기 위한 큐 생성
  const maxY = maps.length; // x의 최대 좌표 값
  const maxX = maps[0].length; // y의 최대 좌표 값
  maps[start[0]][start[1]] = "X"; // 재방문을 막기 위해 시작 지점을 X로 할당

  // queue의 길이가 0보다 큰 경우만 반복, 즉 평가할 다음 좌표가 없는 경우 종료
  while (queue.length > 0) {
    const queueLen = queue.length; // 한 사이클(이동 가능 좌표들)의 순회 횟수인 queue의 길이가 다음 좌표를 쌓을 때 사용하는 push 메소드로 인해 변하기 때문에 해당 값의 고정을 위해 변수로 선언하여 사용

    for (let i = 0; i < queueLen; i++) {
      const [currentY, currentX] = queue.shift(); // 현재 큐에 있는 첫번째 요소를 가져온다. 이동이 완료된 현재 좌표이기 때문에 shift를 통해 추출한 뒤 제거

      // 상하좌우 순으로 다음 좌표를 구하고 이동 여부를 평가하기 위해 4번 사이클을 돌림
      for (let j = 0; j < 4; j++) {
        // 다음 좌표를 구하기 위해 미리 생성해놓은 moveY, moveX를 활용하여 첫번째 사이클에서 상, 두번째 사이클에서 하, 세번째 사이클에서 좌, 네번째 사이클에서 우 순으로 좌표를 더함
        const nextY = currentY + moveY[j];
        const nextX = currentX + moveX[j];

        const isOver = nextY >= maxY || nextX >= maxX; // 이동할 다음 좌표 값이 map의 최대 좌표 값인 maxX 혹은 maxY 보다 큰 경우
        const isUnder = nextY < 0 || nextX < 0; // 이동할 다음 좌표 값이 map의 최소 좌표 값인 0보다 작은 경우
        const isWall = maps[nextY]?.[nextX] === "X"; // 이동할 다음 좌표 값이 벽이거나 이미 방문한 좌표인 경우

        if (isOver || isUnder || isWall) continue; // 3가지 중 하나라도 해당되면 다음 사이클로 넘김

        if (maps[nextY][nextX] === target) return count + 1; // 만약 다음 좌표가 최종적으로 탐색하고 있는 목표라면 현재 까지 카운트 된 값에 현재 이동해야 할 1을 더한 뒤 반환하여 BFS 함수 종료

        queue.push([nextY, nextX]); // 다음 좌표가 이동이 가능한 좌표이므로 queue에 push하여 쌓음, 즉 해당 좌표로 이동
        maps[nextY][nextX] = "X"; // push를 통해 다음 좌표를 queue에 쌓아 해당 좌표로 이동하였기 때문에 해당 좌표에 X를 표시하여 재방문 하지 않도록 함
      }
    }

    count++; // while문의 한 사이클이 끝나면 탐색이 한번 진행되었으므로 count 1 증가
  }

  return -1; // while문 내부에서 다음 좌표로 이동할 수 있는지 평가를 거듭하여 최종적으로 count를 반환하지 못하는 경우, 즉 최종적으로 탐색하고 있는 목표를 만날 수 없는 경우 -1을 반환
};

const mySolution = (maps) => {
  // start 지점과 lever 지점을 찾기 위해 getPosition 유틸 함수 생성 후 해당 함수를 사용하여 위치를 구한다.
  const start = [...getPosition("S", maps)];
  const lever = [...getPosition("L", maps)];

  const leverBfsCount = bfs("L", start, [...maps.map((map) => [...map])]); // lever의 최단 거리 탐색 값을 bfs 함수를 통해 구한 뒤 해당 위치에 도달할 수 없는 경우 -1 반환
  if (leverBfsCount === -1) return -1;

  const exitBfsCount = bfs("E", lever, [...maps.map((map) => [...map])]); // exit의 최단 거리 탐색 값을 bfs 함수를 통해 구한 뒤 해당 위치에 도달할 수 없는 경우 -1 반환
  if (exitBfsCount === -1) return -1;

  return leverBfsCount + exitBfsCount; // 위 조건에 부합하지 않는 경우 두 탐색 값을 더하여 최종 최단 거리 값 반환
};

console.log(mySolution(["SOOOL", "XXXXO", "OOOOO", "OXXXX", "OOOOE"])); // 16
```

주석 참고

<br>
<br>

# 3. 인기 풀이

```tsx
const othersSolution = (maps) => {
  var answer = 0;
  return answer;
};

console.log(othersSolution(["SOOOL", "XXXXO", "OOOOO", "OXXXX", "OOOOE"]));
```

<br>
<br>

# 4. 비교

오늘은 문제를 풀다가 잘 해결되지 않아 다른 개발자 분의 코드를 참고하면서 풀었다. 해당 문제는 전형적인 BFS(너비 우선 탐색) 알고리즘 문제였다. 문제를 짧게 설명하면 시작 지점 S에서 시작하며 O인 경우 이동 가능한 위치이고 X인 경우 이동이 불가능한 벽이다. 이 때 레버 위치인 L을 거쳐 마지막 위치인 E까지 도달하는데 최단 거리를 구하는 것이었다.

풀이 방식은 우선 시작 지점과 레버 위치의 좌표를 구하면서 시작하였다. 해당 좌표들을 기준으로 시작 지점에서 레버 지점까지, 레버 지점에서 목표 지점까지 두 개로 나누어 구한 뒤 해당 값을 더하여 최단 거리를 구하였다. 이 때 각각의 최단 거리를 구하기 위해 BFS 유틸 함수를 사용하였다.

BFS 알고리즘은 우선 상하좌우 이동 거리를 담은 변수를 생성하고 이동 좌표를 쌓기 위한 큐를 생성한 뒤 좌표에서 벗어나는지 체크하는 변수들을 생성하였다. 그 후 while문으로 반복하는데 반복되는 기준은 큐에 탐색할 좌표가 남아있는 경우 반복되도록 하였다.

반복문 내부에서는 for문으로 순회하는데 순회 기준은 상하좌우 순차적으로 값을 더하며 테스트하기 때문에 4번 순회되도록 하였다. for문 내부에서는 미리 생성해놓은 상하좌우 이동 거리를 담은 변수들을 활용하여 사이클 마다 상하좌우 값을 추가하며 다음 좌표가 이동 가능한 좌표인지 확인 후 이동이 불가능하다면 다음 사이클로 넘기고 이동이 가능하다면 목표 지점인지 확인하고 목표 지점이 아니라면 해당 좌표로 이동(큐에 해당 좌표를 쌓음)하도록 하였다.

BFS 구현은 처음이라 다른 개발자 분의 코드를 참고하여 작성하고 주석을 달아 풀이해놓았는데 다음부터는 해당 코드를 학습하여 혼자서 구현할 수 있도록 해야겠다.

<br>
