# **[Algorithm] 프로그래머스 Level 1 - 콜라 문제**

2023년 08월 15일

<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/132267

<br>
<br>

## **2. 나의 풀이**

```tsx
const mySolution = (a, b, n) => {
  var answer = 0;
  let remainingEmptyBottles = n;

  while (remainingEmptyBottles >= a) {
    const quotient = Math.floor(remainingEmptyBottles / a) * b;
    const remainder = remainingEmptyBottles % a;

    remainingEmptyBottles = quotient + remainder;
    answer += quotient;
  }

  return answer;
};

console.log(mySolution(3, 1, 9)); // 4
```

1. 반복문을 돌리는데 빈병의 개수 `remainingEmptyBottles`가 교환을 위해 필요한 빈병의 개수 `a`와 같거나 큰 경우까지만 반복한다.
2. 반복문 내부에서 변수 `quotient`에 교환 후 받을 수 있는 콜라의 개수를 구한다. 현재 가지고 있는 빈병의 개수 `remainingEmptyBottles`를 교환을 위해 필요한 콜라의 개수 `a`와 나눈 뒤 교환 후 받을 수 있는 콜라의 개수 `b`를 곱해주었다.
3. 반복문 내부에서 변수 `remainder`에 교환을 위한 몫을 구할 때 나머지 빈병을 계산한다.
4. 반복문 내부에서 다음 계산을 위한 빈병의 개수를 구하기 위해 교환하여 받은 콜라 `quotient` 와 나머지 빈병 `remainder` 개수를 더하여 `remainingEmptyBottles` 변수에 할당한다.
5. 반복문 내부에서 현재 교환하여 받은 콜라를 카운트하기 위해 `answer` 변수에 누적하여 더한다.

<br>
<br>

## **3. 인기 풀이**

```tsx
const othersSolution = (a, b, n) => {
  return Math.floor((n - b) / (a - b)) * b;
};

console.log(othersSolution(3, 1, 9)); // 4
```

- 참고 : https://blog.naver.com/doctorgu/222992407249

<br>
<br>

## **4. 비교**

나의 풀이와 인기 풀이를 비교해봤을 때 가독성, 처리 속도 등 모든 것을 고려해보아도 무조건 인기 풀이의 압승인 것 같다. 나의 풀이의 경우 순차적으로 반복문을 돌려 해결한 반면 인기 풀이의 경우 기본적인 수학적 접근을 통해 한 줄로 해결하였다.

<br>
