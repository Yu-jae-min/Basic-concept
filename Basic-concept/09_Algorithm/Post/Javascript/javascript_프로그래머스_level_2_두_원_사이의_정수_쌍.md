# [Algorithm] 프로그래머스 Level 2 - 두 원 사이의 정수 쌍

2023년 09월 13일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/181187

<br>
<br>

# 2. 나의 풀이

```tsx
const mySolution = (r1, r2) => {
  return "failed";
};

console.log(mySolution(2, 3)); // 28
```

풀이 실패

<br>
<br>

# 3. 인기 풀이

```tsx
const othersSolution = (r1, r2) => {
  var answer = 0;

  // 1사분면 만을 구한다. 원은 최소 1의 반지름을 가지기 때문에 1로 시작한다. 큰 원의 반지름까지 반복
  for (var x = 1; x <= r2; x++) {
    // x 기준에서 r2만큼 떨어진 y좌표를 구함 -> 이 좌표는 내림이 되어야 한다. -> 큰 값은 쓰지 않기 때문
    var maxY = Math.floor(Math.sqrt(Math.pow(r2, 2) - Math.pow(x, 2))); // 2, 2, 0

    // x 기준에서 r1만큼 떨어진 y좌표를 구함 -> 이 좌표는 올림이 되어야 한다. -> 작은 값은 쓰지 않기 때문
    // 이것은 만약 r1의 길이를 넘어서는 경우가 있는데 이때는 0으로 해준다.
    var minY =
      r1 > x ? Math.ceil(Math.sqrt(Math.pow(r1, 2) - Math.pow(x, 2))) : 0; // 2, 0, 0

    answer += maxY - minY + 1; // 두 개 구한 값의 차 + 1, 1 -> 3 -> 1
  }

  return answer * 4; // 순회 한 후 나머지 사분면들도 똑같기 때문에 이후에 *4를 해준다.
};

console.log(othersSolution(2, 3)); // 28
```

주석 참고

<br>
<br>

# 4. 비교

레벨 2에서 연달아 풀이를 실패했다. 이번 문제도 저번 문제와 마찬가지로 정답률이 37% 밖에 되지 않았다. 처음 해당 문제를 접했을 때는 작은 원의 반지름과 큰 원의 반지름 사이 값 만큼 반복문을 돌리는데 이 때 작은 원의 값을 초기 값으로 설정하고 작은 원의 반지름 값에 반지름 값을 더하고 4를 곱해주어 원의 테두리 점 개수를 구하였다. 그렇게 큰 원과 작은 원 사이의 점의 개수를 구하고자 했는데 역시나 실패해버렸다. 문제를 다시 확인해보니 원의 크기가 정수가 아닐 수도 있다는 조건이 있었다. 계속해서 풀이를 시도했지만 역시나 실패했다. 결국 다른 개발자 분의 풀이를 참고해보았다. 다른 개발자 분의 경우 1사분면에서 큰 원과 작은 원의 좌표를 구한 뒤 두 개의 차를 통해 점의 개수 를 구하였다. 그 후 최종적으로 4를 곱해주는 식으로 문제를 해결하였다.

<br>
