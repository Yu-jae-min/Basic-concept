# **[Algorithm] 프로그래머스 Level 1 - 문자열 나누기**

2023년 08월 27일

<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/140108

<br>
<br>

## **2. 나의 풀이**

```jsx
const mySolution = (s) => {
  let answer = 0;
  let count = 0;
  let baseIndex = 0;

  s.split("").forEach((num, idx) => {
    if (num === s[baseIndex]) {
      count += 1;
    } else {
      count -= 1;
    }

    if (count === 0 || s.length === idx + 1) {
      answer++;
      count = 0;
      baseIndex = idx + 1;
    }
  });

  return answer;
};

console.log(mySolution("banana")); // 3
```

1. 기준이 되는 현재 숫자의 index를 저장할 변수 `baseIndex`, 현재 index의 숫자와 같은 수와 현재 index의 수와 같지 않은 수를 세기 위한 변수 `count`를 생성한다.
2. 기준이 되는 문자를 `split` 메소드로 잘라 배열로 만든 뒤 `forEach`로 반복한다. 이 때 반복문 내부에서는 첫번째 조건문에서 현재 사이클의 숫자와 기준이 되는 숫자가 같은 지 체크한 뒤 `count` 변수를 증가시키거나 감소시킨다.
3. 반복문 내부에서 두번째 조건문에서는 현재 count가 0인 경우, 즉 기준이 되는 숫자와 같은 숫자를 센 카운트 횟수와 기준이 되는 숫자와 같지 않은 숫자를 센 카운트가 같은 경우 `answer`을 증가시킨다. 이 때 이 과정을 반복하기 위해 `count` 변수의 값을 초기화시키고 baseIndex 변수의 값을 현재 idx에 1을 더하여 할당해준다.
4. 두번째 반복문에서 한 가지 조건이 더 추가되는데 현재 사이클이 마지막 문자인 경우 무조건 answer을 카운트해야 하기 때문에 해당 조건을 추가해주었다.
5. 최종적으로 answer을 출력한다.

<br>
<br>

## **3. 인기 풀이**

```jsx
const othersSolution = (s, count = 0) => {
  if (!s) return count;

  let [first, ...rest] = s.split("");
  let countSame = 1;
  let countInSame = 0;
  let i = 0;

  for (; i < rest.length; i++) {
    if (rest[i] === first) countSame++;
    else countInSame++;
    if (countSame === countInSame) break;
  }

  return othersSolution(rest.slice(i + 1).join(""), count + 1);
};

console.log(othersSolution("banana")); // 3
```

1. 첫번째 숫자를 구조 분해하여 분리하고 rest 문법으로 나머지 숫자를 묶어주었다. 그 후 기준이 되는 숫자와 같은 수를 카운트 할 변수 `countSame`, 기준이 되는 숫자와 같지 않은 수를 카운트 할 변수 `countInSame`, 현재 index를 할당 할 변수 `i`를 생성하였다.
2. 카운트 하기 위해 `for` 문으로 반복하는데 반복문 내부에 첫번째 조건에서 `rest` 문법으로 분리한 나머지 숫자 중 현재 index의 number가 기준이 되는 first 숫자와 같은 지 비교 후 같으면 countSame, 아니면 countInSame을 증가시킨다.
3. 반복문 내부에 두번째 조건에서 기준이 되는 숫자와 같은 수를 카운트한 변수의 수와 기준이 되는 숫자와 같지 않은 수를 카운트한 변수의 수가 같아지는 경우 반복문을 빠져나간다.
4. 그 후 재귀 호출하는데 이 때 재귀 함수의 인자로 s와 count를 넘기는데 s의 경우 count가 같아져 잘린 다음 숫자부터 새롭게 순회해야 하므로 `slice` 메소드를 통해 나머지 숫자인 `rest` 배열을 자르는데 인자로 현재 index에 1을 더하여 다음 숫자부터 순회할 수 있도록 해주었다. 그 후 `join`을 통해 문자열로 변환해주었다. 그리고 재귀 호출이 이루어진다는 것은 기준이 되는 숫자와 같은 수를 카운트한 변수와 기준이 되는 숫자와 같지 않은 수가 같은 경우, 즉 문자가 잘리는 경우이기 때문에 기존 count에서 1을 더하여 파라미터로 넘겨준다.
5. 해당 사이클을 반복하여 `slice`로 자른 현재 문자가 없는 경우 `count`를 출력한다.

<br>
<br>

## **4. 비교**

나의 풀이와 인기 풀이의 경우 모두 index 변수, count 변수를 생성 후 반복문을 통해 풀이한 방식은 비슷하였다. 하지만 나의 풀이의 경우 카운트가 증가될 때 단순하게 변수를 초기화 시켜 다음 사이클이 돌 수 있도록 하였고 인기 풀이의 경우 재귀 함수를 사용하였다. 가독성은 비슷하였기 때문에 나의 풀이와 인기 풀이의 속도를 비교해보았다.

```jsx
const random = (length = 8) => {
  const chars = "abcdefghijklmnopqrstuvwxyz";
  let str = "";

  for (let i = 0; i < length; i++) {
    str += chars.charAt(Math.floor(Math.random() * chars.length));
  }

  return str;
};

const randomString = random(1000);
```

위와 같이 랜덤 문자를 반환하는 함수를 생성하여 테스트해보았다. 문제 내부에 제한 사항을 보면 파라미터로 넘어가는 문자열의 길이는 1자 이상 - 10000자 이하였다. 그래서 1000자 정도로 테스트해보았다. 속도는 압도적으로 나의 풀이가 빨랐다. 속도가 최소 30배에서 크게는 180배 이상 차이가 나는 경우도 있었다. 재귀 함수가 얼마나 느린지 알 수 있었다. 재귀 함수는 재귀 함수를 사용하기 자연스러운 흐름일 때 사용한다고 알고 있었다. 하지만 정말 느리기 때문에 (물론 위 상황은 극단적인 상황이지만..) 지금처럼 잘 사용하지는 않을 것 같다.

<br>
