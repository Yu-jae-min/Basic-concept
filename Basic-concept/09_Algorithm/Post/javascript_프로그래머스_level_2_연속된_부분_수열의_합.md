# [Algorithm] 프로그래머스 Level 2 - 연속된 부분 수열의 합

2023년 09월 14일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/178870

<br>
<br>

# 2. 나의 풀이

```tsx
// 테스트 케이스 10~16, 24~30 시간 초과, O(n2)가 원인
const mySolution = (sequence, k) => {
  var answer = [];
  let count = 0;

  for (let i = 0; i < sequence.length; i++) {
    if (sequence[i] > k) {
      break;
    }

    for (let j = i; j < sequence.length; j++) {
      count += sequence[j];

      if (count === k) answer.push({ arr: [i, j], gap: j - i });
      if (count >= k) break;
    }

    count = 0;
  }

  answer.sort((a, b) => a.gap - b.gap);

  return answer[0].arr;
};

console.log(mySolution([1, 2, 3, 4, 5], 7)); // [2, 3]
```

1. count 변수를 생성한다.
2. for문을 중첩하여 사용하는데 이 때 내부 반복문에서의 초기 값은 외부 반복문의 초기 값으로 지정한다. 그 후 반복문을 돌리며 순차적으로 count를 증가시킨다. 그리고 증가 된 count의 값이 k와 같다면 현재 index를 answer 변수에 push 하는데 여러 케이스가 나온다면 index 차이가 적은 index를 반환해야하기 때문에 gap을 함께 담아 객체로 push 한다. 또한 count의 값이 k보다 크거나 같다면 break를 통해 다음 사이클로 넘어갈 수 있도록 한다.
3. 다음 사이클로 넘어가기 전 count를 0으로 초기화해준다.
4. 반복문이 완료되어 k값의 연속된 부분 수열의 합 요소들을 구한 후 여러 케이스가 나오는 경우 index 차가 적은 요소를 반환해야하므로 sort를 사용해서 gap값을 기준으로 오름차순 정렬해준다.
5. 최종적으로 오름차순 정렬된 배열 중 첫번째 요소의 arr를 반환한다.

<br>
<br>

# 3. 인기 풀이

```tsx
// 투 포인터 알고리즘
const othersSolution = (sequence, k) => {
  var answer = [0, sequence.length - 1];
  let left = 0;
  let right = 0;
  let sum = sequence[left];

  while (right < sequence.length) {
    if (sum > k) {
      sum -= sequence[left];
      left++;
    } else if (sum < k) {
      right++;
      sum += sequence[right];
    } else {
      let distance = answer[1] - answer[0];
      let currentDistance = right - left;

      if (distance > currentDistance) {
        answer = [left, right];
      }

      sum -= sequence[left];
      left++;
    }
  }

  return answer;
};

console.log(othersSolution([1, 2, 3, 4, 5], 7)); // [2, 3]
```

1. answer 배열 내부에 초기 index를 할당하는데 투 포인터 알고리즘을 활용하므로 index의 시작 값과 끝 값을 나누어 할당한다.
2. 투 포인터 알고리즘을 구현하기 위한 left 변수와 right 변수를 생성한다. 이 변수들이 index가 되는 것이다.
3. sum 변수에 기준이 되는 left index의 값을 할당한다.
4. while문을 통해 반복하는데 이 때 right index 값이 sequence 배열의 요소 길이보다 작을 때까지 반복한다.
5. 반복문 내부의 조건은 현재 합 sum이 k보다 큰 경우, 작은 경우, 같은 경우로 나뉜다. 현재 합이 k보다 큰 경우는 현재 left 포인터의 값을 현재 합에서 빼준 뒤 left 포인터를 증가시킨다.
6. 현재 합이 k보다 작은 경우는 right 포인터를 증가시킨 뒤 해당 포인터의 값을 현재 합에 더해준다.
7. 현재 합이 k와 같은 경우 기존 두 포인터와 현재 두 포인터의 차를 구하여 비교해준다. 비교하는 이유는 두 차가 적은 수가 우선적으로 출력되어야 하기 때문이다. 만약 현재 두 포인터의 차가 기존 두 포인터의 차보다 작은 경우 현재 포인터의 값으로 새로 할당한다. 그 후 다음 사이클 진행 전 현재 left 포인터의 값을 현재 합에서 빼준 뒤 left 포인터를 증가시킨다.
8. 최종적으로 answer을 출력한다.

<br>
<br>

# 4. 비교

레벨 2에서 오랜만에 코드 풀이는 성공했다. 그런데 역시나 O(n2)의 시간복잡도를 가지는 로직으로는 시간초과가 발생했다. 나의 풀이의 경우 중첩 반복문을 사용해서 외부 반복문에서는 시작 index를 증가시켰고 내부 반복문에서는 시작 index를 기준으로 배열의 끝까지 순차적으로 탐색하여 값을 증가시키고 조건을 걸어 부분 수열의 합에 부합하는 요소들을 구하였다. 하지만 역시 중첩 반복문으로는 테스트 케이스 모두 통과할 수는 없었다. 왜냐하면 문제 조건 중 sequence 파라미터의 최대 길이는 100만이 되는데 반복문의 기준으로 사용되는 sequence 파라미터가 중첩으로 사용되기 때문에 실패할 수 밖에 없었던 것 같다. 그렇기 때문에 해당 문제는 무조건 O(n)의 시간복잡도로 풀어야했다. 해당 문제를 해결한 다른 개발자 분들의 경우 O(n)의 시간복잡도로 문제를 해결하기 위해 투 포인터 알고리즘을 활용했다. 투 포인터 알고리즘을 활용하여 left, right의 포인터가 이동할 때마다 가감하여 연산하는 방식을 통해 중복 연산을 제거하도록 하였다.

<br>
