# [Algorithm] 프로그래머스 Level 2 - 호텔 대실

2023년 09월 24일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/155651

<br>
<br>

# 2. 나의 풀이

```tsx
const mySolution = (book_time) => {
  book_time = book_time
    .map(([startTime, endTime]) => {
      const [startHour, startMinute] = startTime
        .split(":")
        .map((t) => Number(t));
      const [endHour, endMinute] = endTime.split(":").map((t) => Number(t));

      const start = startHour * 60 + startMinute;
      const end = endHour * 60 + endMinute + 10;

      return [start, end];
    })
    .sort((a, b) => a[0] - b[0]);

  const rooms = [book_time.shift()];

  while (book_time.length) {
    const nextTime = book_time.shift();
    let isChange = false;

    for (let i = 0; i < rooms.length; i++) {
      if (rooms[i][1] <= nextTime[0]) {
        rooms[i] = nextTime;
        isChange = true;
        break;
      }
    }

    if (!isChange) rooms.push(nextTime);
  }

  return rooms.length;
};

console.log(
  mySolution([
    ["15:00", "17:00"],
    ["16:40", "18:20"],
    ["14:20", "15:20"],
    ["14:10", "19:20"],
    ["18:20", "21:20"],
  ])
); // 3
```

1. map 메소드를 사용하여 전달받은 예약 시간이 담긴 파라미터 book_time의 각 요소 값을 분 단위로 변환 및 number 타입으로 변환한다. 이 때 룸 사용 후 10분 간 룸을 청소해야 하기 때문에 배정을 할 수 없으므로 종료 시간에 10분을 추가해준다.
2. map 메소드를 사용하여 변환한 예약 시간이 담긴 파라미터 book_time를 예약 시작 시간 기준으로 오름차순 정렬한다.
3. 방을 배정하기 위한 변수 room을 생성한 뒤 shift 메소드를 사용하여 book_time 배열 중 첫번째 요소를 할당한다.
4. while문을 통해 반복문을 돌리는데 조건은 예약 시간이 담긴 파라미터 book_time의 length가 없을 때까지 반복한다.
5. 반복문 내부에서 shift 메소드를 통해 다음 예약 시간을 추출하고 기존 방에 배정되었는지를 체크할 변수 isChange를 생성한다.
6. for문으로 반복하는데 이 때 반복 기준은 방을 배정한 rooms 변수의 length를 기준으로 반복한다. 이 때 반복문 내부에서는 만약 현재 배정 된 방의 예약 시간의 종료 시간(청소 시간 포함)이 다음 예약 시간의 시작 시간과 같거나 작은 경우 해당 방에 다음 예약 시간을 할당한 뒤 isChange 변수를 true로 바꿔주고 break로 반복문을 종료한다.
7. for문 종료 후 isChange가 false라면, 즉 기존 방에 다음 예약 시간을 배정할 수 없다면 새로운 방 배정을 위해 rooms에 다음 예약 시간을 push 한다.
8. 최종적으로 rooms의 length를 반환한다.

<br>
<br>

# 3. 인기 풀이

```tsx
function makeMinStamp(time) {
  const [hour, min] = time.split(":").map((v) => Number(v));

  return hour * 60 + min;
}

const othersSolution = (book_time) => {
  const timeArr = Array.from({ length: makeMinStamp("23:59") + 10 }, () => 0);

  book_time.forEach((time, i) => {
    const [s, e] = time;
    let start = makeMinStamp(s);
    const end = makeMinStamp(e) + 9;

    for (start; start <= end; start++) {
      timeArr[start]++;
    }
  });

  return Math.max(...timeArr);
};

console.log(
  othersSolution([
    ["15:00", "17:00"],
    ["16:40", "18:20"],
    ["14:20", "15:20"],
    ["14:10", "19:20"],
    ["18:20", "21:20"],
  ])
); // 3
```

1. 예약 시간을 분 단위로 변경하기 위한 유틸 함수 makeMinStamp 생성
2. Array from을 통해 1일 시간에 청소 시간을 더한 만큼 배열 요소를 생성하고 0으로 초기화한다. 해당 배열은 예약 시간을 stamp로 표시하기 위한 배열이다.
3. 예약 시간이 담긴 파라미터 book_time를 forEach문으로 반복한다. 이 때 반복문 내부에서 우선 현재 예약 시간의 시작 시간과 종료 시간을 분으로 변환하는데 종료 시간에는 청소 시간을 포함시킨다. 그 후 for문으로 반복문을 돌리는데 현재 예약 시간의 시작 시간부터 예약 종료 시간까지 해당 값을 index로 사용하여 timeArr 내부 요소를 증가시킨다.
4. 최종적으로 가장 많은 stamp가 찍힌 요소의 값을 반환한다.

<br>
<br>

# 4. 비교

우선 프로그래머스 레벨 2 알고리즘을 처음으로 모든 테스트 케이스를 한 번에 통과했다. 이것만으로도 너무나 기쁘다. 풀이 속도도 나의 풀이가 더 빨랐다. 하지만 풀이 방식의 정확도는 인기 풀이가 더 좋았다고 느낀다. 나의 풀이의 경우 예약 시간을 순차적으로 배열 요소로 담아주면서 기존에 담긴 예약 시간의 종료 시간이 다음 예약 시간의 시작 시간보다 빠르거나 같은 경우 해당 배열 요소를 바꿔주는 방식으로 풀이하였다. 반면 인기 풀이의 경우 문제에서 입출력 예시로 제시해준 아래 이미지를 그대로 풀어낸 것 같이 풀이하였다.

![Algorithm_프로그래머스_Level_2_호텔_대실_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/d909fa99-b3da-457d-bf0b-b3d99d95aa17)

우선 나와 마찬가지로 시간의 비교를 위해서 분 단위로 변환하는 유틸 함수를 생성하였고 예약 시간을 표시할 배열을 생성한 뒤 해당 배열에 현재 예약 시간의 index를 증가시켰다. 그 후 최종적으로 가장 많은 stamp가 찍힌 시간을 반환하였다. 해당 풀이를 보며 문제에서 요구하는 풀이 방식을 정확하게 구현했다고 느꼈다. 나의 풀이가 인기 풀이보다 속도는 더 빨랐는데 그 이유는 인기 풀이 내부에 while문 안에서 for문으로 time stamp를 찍고 있는데 이 때 분 단위로 for문이 돌아가기 때문에 순회 횟수가 많아져 속도는 나의 풀이가 더 나았던 것 같다. 그래도 레벨 2 문제를 풀며 처음으로 한 번에 통과할 수 있어서 좋았다.

<br>
