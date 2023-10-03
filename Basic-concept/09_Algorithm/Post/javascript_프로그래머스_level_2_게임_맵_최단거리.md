# [Algorithm] 프로그래머스 Level 2 - 게임 맵 최단거리

2023년 10월 03일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/1844

<br>
<br>

# 2. 나의 풀이

```tsx
const mySolution = (maps) => {
  var count = 1; // 한 칸 이동할 때마다 누적하여 증가시킬 변수 생성, 첫 칸도 포함되므로 초기 값은 1
  const nx = [0, 0, -1, 1]; // 좌, 우 이동 좌표
  const ny = [-1, 1, 0, 0]; // 상, 하 이동 좌표
  const lx = maps[0].length; // x의 최대 좌표 값
  const ly = maps.length; // y의 최대 좌표 값
  let queue = [[0, 0]]; // 현재 이동 좌표가 담긴 배열을 쌓기 위한 큐 생성
  maps[0][0] = 0; // 재방문을 막기 위해 시작 지점을 0으로 할당

  while (queue.length > 0) {
    const queueLen = queue.length; // 하단 for문 내부에서 push로 인해 queue의 기링가 변하기 때문에 미리 변수에 할당

    for (let i = 0; i < queueLen; i++) {
      const [currentY, currentX] = queue.shift(); // 큐에 쌓여있는 첫번째 요소 추출

      for (let j = 0; j < 4; j++) {
        // 다음 좌표를 구하기 위해 미리 생성해놓은 ny, nx를 활용하여 첫번째 사이클에서 상, 두번째 사이클에서 하, 세번째 사이클에서 좌, 네번째 사이클에서 우 순으로 좌표를 더함
        const nextY = currentY + ny[j];
        const nextX = currentX + nx[j];

        const isOver = nextY >= ly || nextX >= lx; // 이동할 다음 좌표 값이 map의 최대 좌표 값인 maxX 혹은 maxY 보다 큰 경우
        const isUnder = nextY < 0 || nextX < 0; // 이동할 다음 좌표 값이 map의 최소 좌표 값인 0보다 작은 경우
        const isWall = maps[nextY]?.[nextX] === 0; // 이동할 다음 좌표 값이 벽이거나 이미 방문한 좌표인 경우
        const isFinish = nextX === lx - 1 && nextY === ly - 1; // 이동할 다음 좌표 값이 목표 좌표 값인 경우

        if (isOver || isUnder || isWall) continue; // 3가지 중 하나라도 해당되면 다음 사이클로 넘김
        if (isFinish) return count + 1; // 만약 다음 좌표가 최종적으로 탐색하고 있는 목표라면 현재 까지 카운트 된 값에 현재 이동해야 할 1을 더한 뒤 반환하여 BFS 함수 종료

        queue.push([nextY, nextX]); // 다음 좌표가 이동이 가능한 좌표이므로 queue에 push하여 쌓음, 즉 해당 좌표로 이동
        maps[nextY][nextX] = 0; // push를 통해 다음 좌표를 queue에 쌓아 해당 좌표로 이동하였기 때문에 해당 좌표에 0을 표시하여 재방문 하지 않도록 함
      }
    }

    count++; // while문의 한 사이클이 끝나면 탐색이 한번 진행되었으므로 count 1 증가
  }

  return -1; // while문 내부에서 다음 좌표로 이동할 수 있는지 평가를 거듭하여 최종적으로 count를 반환하지 못하는 경우, 즉 최종적으로 탐색하고 있는 목표를 만날 수 없는 경우 -1을 반환
};

console.log(
  mySolution([
    [1, 0, 1, 1, 1],
    [1, 0, 1, 0, 1],
    [1, 0, 1, 1, 1],
    [1, 1, 1, 0, 1],
    [0, 0, 0, 0, 1],
  ])
); // 11
```

주석 참고

<br>
<br>

# 3. 인기 풀이

```tsx
const othersSolution = (maps) => {
  var yLen = maps.length - 1;
  var xLen = maps[0].length - 1;

  var queue = [[0, 0]];

  var visited = Array.from(new Array(maps.length), () =>
    new Array(maps[0].length).fill(false)
  );

  var result = 0;

  while (queue.length) {
    result++;
    var size = queue.length;
    for (var i = 0; i < size; i++) {
      var point = queue.shift();
      var curY = point[0];
      var curX = point[1];

      if (visited[curY][curX]) continue;

      maps[curY][curX] = 0;

      visited[curY][curX] = true;

      if (curY === yLen && curX === xLen) return result;

      if (curY < yLen && maps[curY + 1][curX] === 1)
        queue.push([curY + 1, curX]);
      if (curX < xLen && maps[curY][curX + 1] === 1)
        queue.push([curY, curX + 1]);
      if (curY > 0 && maps[curY - 1][curX] === 1) queue.push([curY - 1, curX]);
      if (curX > 0 && maps[curY][curX - 1] === 1) queue.push([curY, curX - 1]);
    }
  }

  return -1;
};

console.log(
  othersSolution([
    [1, 0, 1, 1, 1],
    [1, 0, 1, 0, 1],
    [1, 0, 1, 1, 1],
    [1, 1, 1, 0, 1],
    [0, 0, 0, 0, 1],
  ])
); // 11
```

나의 풀이와 비슷하다.

<br>
<br>

# 4. 비교

해당 문제는 이전에 풀었던 문제와 비슷했다. BFS(너비 우선 탐색) 알고리즘을 활용해야하는 문제이다. 나의 풀이와 인기 풀이의 풀이 방식은 거의 비슷했다.

다음 포지션(방문할 수 있는 노드)을 쌓기 위한 큐를 생성한 뒤 이동할 수 있는 포지션을 각각 큐에 쌓는다. 예를 들어 상하좌우 중 상과 우로 이동할 수 있다면 큐에 상으로 이동한 포지션, 우로 이동한 포지션을 각각 쌓는 것이다. 그 후 큐에 쌓인 각 포지션들은 자기 자신의 위치를 기준으로 다음 이동할 수 있는 포지션을 확인한다. 해당 작업을 반복하여 가장 먼저 최종 지점에 도착하는 포지션이 있다면 해당 카운트를 반환하는 방식으로 풀이하였다. 즉 쉽게 말해 지름길과 돌아가는 길이 있다면 지름길의 경로와 돌아가는 길 경로를 모두 확인하는데 이 때 지름길이 목표 지점에 먼저 도착하기 때문에 지름길이 도착하는 순간 카운트를 반환하며 함수를 종료하는 것이다.

해당 문제를 작성하며 헷갈리는 부분이 있어 이전에 해석했던 코드를 조금씩 참고하며 풀이하였다. 물론 참고했다는 점에서 마이너스를 줄 수 있겠지만 BFS 알고리즘을 더 이해할 수 있었던 것 같다.

<br>
