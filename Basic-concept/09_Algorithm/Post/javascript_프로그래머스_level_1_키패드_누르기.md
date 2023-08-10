# **[Algorithm] 프로그래머스 Level 1 - 키패드 누르기**

2023년 08월 11일

<br>
<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/67256

<br>
<br>

## **2. 나의 풀이**

```tsx
const mySolution = (numbers, hand) => {
  var answer = "";

  const keyPad = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
    ["*", 0, "#"],
  ];

  // 손가락의 초기 위치 or 이전 위치
  const beforePosition = {
    left: [3, 0],
    right: [3, 2],
  };

  numbers.forEach((num) => {
    keyPad.forEach((key, index) => {
      // 숫자가 아닌 경우 return
      if (!key.includes(num)) return;

      const currentVerticalPosition = index;
      const currentHorizontalPosition = key.indexOf(num);
      const currentPosition = [
        currentVerticalPosition,
        currentHorizontalPosition,
      ];

      // 현재 num이 keyPad index 중 0인 경우, 즉 왼손으로 눌러야 하는 경우
      if (currentHorizontalPosition === 0) {
        beforePosition.left = currentPosition;
        return (answer = answer + "L");
      }

      // 현재 num이 keyPad index 중 2인 경우, 즉 오른손으로 눌러야 하는 경우
      if (currentHorizontalPosition === 2) {
        beforePosition.right = currentPosition;
        return (answer = answer + "R");
      }

      // 현재 num이 keypad index 중 1인 경우, 즉 왼손과 오른손 중 가까운 손으로 눌러야 하는 경우
      // lVD, rVD, lHD, rHD : 현재 포지션을 기준으로 이전 포지션과 차이 값 계산 후 합산하여 조건으로 활용
      const lVD = Math.abs(currentVerticalPosition - beforePosition.left[0]);
      const rVD = Math.abs(currentVerticalPosition - beforePosition.right[0]);
      const lHD = Math.abs(currentHorizontalPosition - beforePosition.left[1]);
      const rHD = Math.abs(currentHorizontalPosition - beforePosition.right[1]);

      // 오른손의 거리가 더 먼 경우
      if (lVD + lHD < rVD + rHD) {
        beforePosition.left = currentPosition;
        return (answer = answer + "L");
      }

      // 왼손의 거리가 더 먼 경우
      if (lVD + lHD > rVD + rHD) {
        beforePosition.right = currentPosition;
        return (answer = answer + "R");
      }

      // 떨어진 거리가 동일한 경우
      beforePosition[hand] = currentPosition;
      return (answer = answer + hand[0].toUpperCase());
    });
  });

  return answer;
};

console.log(mySolution([1, 3, 4, 5, 8, 2, 1, 4, 5, 9, 5], "right"));
```

코드 내부에 주석으로 풀이해놓았다. 키패드 모양으로 배열을 생성한 뒤 해당 배열의 `index`를 활용하여 이전 손가락 위치의 값을 갱신하였다. 그 후 두 손가락을 결정해야하는 조건(2, 5, 8, 0)인 경우 이 위치 값을 활용하여 현재 위치에서 가까운 손가락으로 키패드를 누를 수 있도록 하였다.

<br>
<br>

## **3. 인기 풀이**

```tsx
const othersSolution = (numbers, hand) => {
  hand = hand[0] === "r" ? "R" : "L";
  // 키패드의 세로축 거리를 계산하기 위한 숫자이다. 누르는 숫자가 0인 경우 1, 1~3인 경우 4, 4~6인 경우 3, 7~9인 경우 2를 나타낸다.
  let position = [1, 4, 4, 4, 3, 3, 3, 2, 2, 2];
  let h = { L: [1, 1], R: [1, 1] };
  return numbers
    .map((x) => {
      if (/[147]/.test(x)) {
        h.L = [position[x], 1];
        return "L";
      }
      if (/[369]/.test(x)) {
        h.R = [position[x], 1];
        return "R";
      }
      // 거리를 계산한다. 현재 위치에서 이전 위치를 빼준 뒤 h.L[1]을 더한다. h.L[1]을 더해주는 이유는 가로축 거리를 더해주기 위함이다.
      let distL = Math.abs(position[x] - h.L[0]) + h.L[1];
      let distR = Math.abs(position[x] - h.R[0]) + h.R[1];
      // 떨어진 거리가 같은 경우
      if (distL === distR) {
        h[hand] = [position[x], 0];
        return hand;
      }
      // 오른손의 거리가 더 먼 경우
      if (distL < distR) {
        h.L = [position[x], 0];
        return "L";
      }
      // 왼손의 거리가 더 먼 경우
      h.R = [position[x], 0];
      return "R";
    })
    .join("");
};
```

키패드 세로축 거리를 계산하기 위한 배열을 생성한 뒤 해당 값을 사용하여 거리를 계산하였다. 또한 정규식을 활용하여 조건을 할당하기도 하였다.

<br>
<br>

## **4. 비교**

나의 풀이와 인기 풀이의 큰 차이점은 추가적인 반복문이 없다는 것이다. 세로축 거리를 계산하는 배열을 만들어 추가적인 반복문 사용을 자제하였다. 또한 정규식을 활용하여 조건을 단순화하였다. 하지만 `position` 배열 요소를 보았을 때 처음에 이게 어떤 의미를 지닌 요소인지 바로 알 수 없었다. 개인적으로 가독성 부분에서는 나의 풀이가 조금 더 낫지 않나라는 생각을 하였지만 중첩 반복문을 사용하지 않았다라는 점에서는 인기 풀이가 더 좋은 코드라고 생각된다.

<br>
