# [Algorithm] 프로그래머스 Level 2 - 다음 큰 숫자

2023년 10월 02일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/12911

<br>
<br>

# 2. 나의 풀이

```tsx
const oneBitLength = (number) => {
  return [...number.toString(2)].filter((bit) => bit === "1").length;
};

const mySolution = (n) => {
  var answer = n;
  const baseOneBitLength = oneBitLength(n);

  while (true) {
    answer++;
    const nextOneBitLength = oneBitLength(answer);
    if (baseOneBitLength === nextOneBitLength) break;
  }

  return answer;
};

console.log(mySolution(78)); // 83
```

1. answer 변수에 파라미터로 전달받은 숫자 n을 복사한다.
2. 유틸 함수 oneBitLength를 생성하는데 해당 함수는 파라미터로 숫자를 전달받고 해당 숫자를 2진수로 만든 뒤 filter 메소드를 사용하여 1bit를 찾아 배열로 반환한 뒤 length로 길이를 반환한다.
3. 유틸 함수 oneBitLength를 사용하여 기준이 되는 파라미터 n의 1bit 개수를 찾는다.
4. while문을 통해 반복하는데 조건은 true로 설정하여 계속해서 반복되도록 한다. 이 때 반복문 내부에서는 다음 비교 대상을 증가시키기 위해 증감연산자를 통해 answer을 증가시키고 유틸 함수 oneBitLength를 사용하여 비교 대상이 되는 파라미터 answer의 1bit 개수를 찾는다. 그 후 기준이 되는 파라미터의 1bit 개수와 비교 대상이 되는 파라미터 answer의 1bit 개수가 같은 경우 반복문을 종료시킨다.

<br>
<br>

# 3. 인기 풀이

```tsx
const othersSolution = (n, a = n + 1) => {
  return n.toString(2).match(/1/g).length == a.toString(2).match(/1/g).length
    ? a
    : othersSolution(n, a + 1);
};

console.log(othersSolution(78)); // 83
```

1. 전달받은 파라미터 숫자 n과 추가로 a 파라미터를 추가하는데 초기 값은 n + 1로 설정한다. 이유는 비교할 다음 대상 값이 해당 파라미터의 값이기 때문이다.
2. 기준이 되는 파라미터 n과 다음 비교대상 a를 toString을 통해 10진수를 2진수로 변환하고 match 메소드를 통해 1bit를 찾아 배열로 반환한 뒤 length로 길이를 찾는다.
3. 두 값이 같은 경우 해당 값 a를 반환하고 아닌 경우 재귀 호출하는데 파라미터는 현재 비교대상 값에 1을 추가하여 호출한다.

<br>
<br>

# 4. 비교

해당 문제의 조건은 아래와 같다.

- 조건 1. n의 다음 큰 숫자는 n보다 큰 자연수 입니다.
- 조건 2. n의 다음 큰 숫자와 n은 2진수로 변환했을 때 1의 갯수가 같습니다.
- 조건 3. n의 다음 큰 숫자는 조건 1, 2를 만족하는 수 중 가장 작은 수 입니다.

위 조건을 보며 처음에는 파라미터로 전달받은 숫자를 2진수로 변환하고 2진수를 계속해서 증가시키려는 말도안되는 생각을 했다. 하지만 2진수로 변환 전 기준이 되는 숫자에서 1씩 증가시키며 1bit의 개수가 같은 경우 해당 값을 반환하는 방법으로 풀이하게 되었다.

나의 풀이와 인기 풀이의 경우 풀이 방식 자체는 유사했다. 우선 기준이 되는 파라미터 n을 2진수로 변환하고 1bit의 개수를 구하였다. 그리고 비교 대상이 되는 파라미터를 2진수로 변환하고 1bit의 개수를 구한 뒤 두 값을 비교하여 같다면 해당 비교 대상을 반환하고 아니라면 비교 대상을 증가시켜 다시 1bit의 개수를 구해 비교하는 방식으로 반복하였다. 하지만 구현하는 방식은 달랐다. 나의 풀이의 경우 유틸 함수, while문을 사용하여 로직을 작성하였고 인기 풀이의 경우 match 메소드, 재귀 함수 등을 통해 구현하였다.

두 풀이를 비교해보면 가독성은 인기 풀이가 더 간결해보였다. 또한 속도에서도 인기 풀이가 조금 더 빨랐다. 나는 재귀 함수의 경우 호출될 때마다 stack 메모리를 사용하기 때문에 성능이 좋지 않다는 생각을 가지고 있어 잘 사용하지 않았다. 하지만 이 문제와 같이 반복되는 횟수를 예측하기 어렵고 사용하는 메모리가 적은 경우 재귀 함수 사용이 더 자연스럽게 표현이 가능하다고 느꼈다.

<br>
