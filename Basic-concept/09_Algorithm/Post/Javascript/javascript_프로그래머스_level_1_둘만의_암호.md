# [Algorithm] 프로그래머스 Level 1 - 둘만의 암호

2023년 08월 30일

<br>

## 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/155652

<br>
<br>

## 2. 나의 풀이

```jsx
const mySolution = (s, skip, index) => {
  var answer = "";
  const baseChars = "abcdefghijklmnopqrstuvwxyz";
  const filterChars = [...baseChars]
    .filter((str) => !skip.includes(str))
    .join("");

  [...s].forEach((str) => {
    let currnetIndex = filterChars.indexOf(str) + index;

    if (currnetIndex > filterChars.length - 1) {
      currnetIndex = currnetIndex % filterChars.length;
    }

    answer += filterChars[currnetIndex];
  });

  return answer;
};

console.log(mySolution("aukks", "wbqd", 5)); // "happy"
```

1. 기준이 되는 영문 소문자 집합 문자열 `baseChars` 변수를 생성하였다.
2. 파라미터로 넘어오는 skip의 문자열은 포함되면 안되기 때문에 `filter` 메소드를 활용하여 기준이 되는 `baseChars` 문자열을 필터처리하는데 이 때 필터 조건은 `includes` 메소드를 활용하여 skip에 포함되어 있는지 여부를 체크하여 필터 된 영문 소문자 집합 문자열 `filterChars`를 생성하였다.
3. 변환해야하는 문자열 `s`를 스프레드 문법을 통해 배열로 변환 후 `forEach` 메소드로 반복하였다. 이 때 반복문 내부에서는 `indexOf` 메소드를 활용하여 filterChars를 기준으로 현재 문자열의 index를 찾은 뒤 파라미터로 전달받은 index 만큼 더하여 밀린 index `currentIndex`를 구하였다.
4. `if` 조건문을 활용하여 밀린 index `currentIndex` 가 필터 된 영문 소문자 집합 문자열 `filterChars` 에서 1을 뺸 값보다 큰 경우 `filterChars` 가 가지고 있는 문자열 index를 초과하는 것이기 때문에 해당 index를 filterChars의 길이로 나눈 나머지 값을 활용하여 새로운 index를 구하였다. 이 때 빼기 `-`를 활용하지 않고 나머지 `%`를 활용한 이유는 skip의 문자열이 매우 길어 사용할 수 있는 알파벳이 적을 때 기준 index에 추가되는 값인 파라미터 index가 크게 된다면 filterChars가 가지고 있는 index를 여전히 초과할 수 있기 때문에 나머지 값으로 구현하였다.
5. 그 후 반복문 내부에서 answer 변수에 해당 문자열이 밀린 문자를 filterChars에서 찾아 누적해서 더해주었다.
6. 최종적으로 answer 변수를 출력하였다.

<br>
<br>

## 3. 인기 풀이

```jsx
const othersSolution = (s, skip, index) => {
  const alphabet = [
    "a",
    "b",
    "c",
    "d",
    "e",
    "f",
    "g",
    "h",
    "i",
    "j",
    "k",
    "l",
    "m",
    "n",
    "o",
    "p",
    "q",
    "r",
    "s",
    "t",
    "u",
    "v",
    "w",
    "x",
    "y",
    "z",
  ].filter((c) => !skip.includes(c));

  return s
    .split("")
    .map((c) => alphabet[(alphabet.indexOf(c) + index) % alphabet.length])
    .join("");
};

console.log(othersSolution("aukks", "wbqd", 5)); // "happy"
```

1. 기준이 되는 영문 소문자 집합 문자열 `alphabet` 변수를 배열로 생성하였다. 그 후 파라미터로 넘어오는 skip의 문자열은 포함되면 안되기 때문에 `filter` 메소드를 활용하여 해당 배열을 필터 처리하는데 이 때 필터 조건은 `includes` 메소드를 활용하여 skip에 포함되어 있는지 여부를 체크하여 필터 된 영문 소문자 집합 문자열 배열을 생성하였다.
2. 변환해야하는 문자열 `s`를 `split` 메소드를 통해 배열로 변환 후 `map` 메소드를 사용하여 각 요소를 변환하였다. 이 때 map 메소드 내부에서는 `indexOf` 메소드를 활용하여 `alphabet`를 기준으로 현재 문자열의 index를 찾은 뒤 파라미터로 전달받은 index 만큼 더하여 밀린 index를 구하고 해당 값을 `alphabet`의 길이로 나눈 나머지 값을 활용하여 최종적으로 밀리는 index를 구하였다. 그 후 `alphabet` 배열의 최종적으로 밀리는 index 값을 활용하여 밀린 문자로 변환되도록 하였다.
3. 최종적으로 `join` 메소드를 활용하여 문자열로 변환 후 출력하였다.

<br>
<br>

## 4. 비교

나의 풀이와 인기 풀이의 경우 큰 차이가 없었다. 둘 다 현재 요소를 반복하는 forEach 혹은 map 메소드를 활용하였고 내부에서 동일한 조건을 활용하여 최종적으로 밀리는 index를 구하여 변환되는 문자를 찾았다. 풀이 방식은 완전 동일했지만 나의 경우 기준 알파벳 문자열을 string 형식으로 생성해놓고 배열로 변환하여 작업하였는데 인기 풀이의 경우 애초에 array로 생성하여 작업하였다. 나의 경우 코드의 길이가 길어지면 가독성이 떨어질 것이라고 생각하여 string으로 생성하였었는데 규칙적인 알파벳이기 때문에 크게 가독성을 해치는 것 같다. 인기 풀이와 같이 애초에 array로 생성해놓았다면 필요없는 스프레드 문법의 사용이나 변수 생성을 억제할 수 있었을 것 같다.

<br>
