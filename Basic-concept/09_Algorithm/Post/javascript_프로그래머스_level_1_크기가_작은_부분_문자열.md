# [Algorithm] 프로그래머스 Level 1 - 크기가 작은 부분 문자열

2023년 08월 29일

<br>

## 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/147355

<br>
<br>

## 2. 나의 풀이

```jsx
const mySolution = (t, p) => {
  var answer = 0;

  for (let i = 0; i <= t.length - p.length; i++) {
    if (Number(t.slice(i, i + p.length)) <= Number(p)) answer++;
  }

  return answer;
};

console.log(mySolution("3141592", "271")); // 2
```

1. `for 반복문`을 사용하여 반복하였다. 이 때 반복 조건은 길이를 잘라 비교할 문자열 t의 길이에서 비교 기준이 되는 문자열 p의 길이를 뺀 수와 현재 index가 같거나 작을 때까지 반복하였다.
2. 반복문 내부에서 조건문을 활용하여 특정 조건에서 `answer` 변수를 카운트하여 증가시키는데, 조건은 길이를 잘라 비교할 문자열 t를 slice 메소드를 활용하여 자르는데 이 때 현재 index부터 비교 기준이 되는 문자열 p의 길이만큼 잘라주었다. 그 후 `Number` 함수를 통해 number 타입으로 변환하여 비교한 뒤 증가시켰다.

<br>
<br>

## 3. 인기 풀이

```jsx
const othersSolution = (t, p) => {
  let count = 0;

  for (let i = 0; i <= t.length - p.length; i++) {
    let value = t.slice(i, i + p.length);
    if (+p >= +value) count++;
  }

  return count;
};

console.log(othersSolution("3141592", "271")); // 2
```

1. `for 반복문`을 사용하여 반복하였다. 이 때 반복 조건은 길이를 잘라 비교할 문자열 t의 길이에서 비교 기준이 되는 문자열 p의 길이를 뺀 수와 현재 index가 같거나 작을 때까지 반복하였다.
2. 반복문 내부에서 조건문을 활용하여 특정 조건에서 `count` 변수를 카운트하여 증가시키는데, 조건은 길이를 잘라 비교할 문자열 t를 slice 메소드를 활용하여 자르는데 이 때 현재 index부터 비교 기준이 되는 문자열 p의 길이만큼 잘라주었다. 그 후 `+` 기호를 붙여 number 타입으로 변환하여 비교한 뒤 증가시켰다.

<br>
<br>

# 4. 비교

나의 풀이와 인기 풀이의 경우 큰 차이가 없었다. 둘 다 반복문을 사용하였고 slice 메소드로 자르는 것 까지 동일했다. 유일한 차이점은 number 타입으로 변환하는데 있었다. 나의 경우 Number 함수를 사용하여 타입을 변경하였고 인기 풀이의 경우 + 기호를 붙여 타입을 변환하였다.

<br>
