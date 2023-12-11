# **[Algorithm] 프로그래머스 Level 1 - 숫자 문자열과 영단어**

2023년 07월 26일

<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/81301

<br>
<br>

## **2. 나의 풀이**

```jsx
const solution = (s) => {
  let answer = s;

  const numberList = [
    "zero",
    "one",
    "two",
    "three",
    "four",
    "five",
    "six",
    "seven",
    "eight",
    "nine",
  ];

  numberList.forEach((num, idx) => {
    answer = answer.replaceAll(num, idx);
  });

  return Number(answer);
};

console.log(solution("1zerotwozero3"));
```

숫자 string이 들어간 배열을 만들고 순회하며 파라미터를 치환하였다. 첫 풀이 시 `replace`를 사용했는데 중복 문자(ex sevenseven)에서 이슈가 발생했다. 그래서 전체를 치환하기 위해 `repalceAll`을 사용하였다.

<br>
<br>

## **3. 다른 개발자 분의 풀이**

```jsx
const solution = (s) => {
  const numberList = [
    "zero",
    "one",
    "two",
    "three",
    "four",
    "five",
    "six",
    "seven",
    "eight",
    "nine",
  ];

  var answer = s;

  for (let i = 0; i < numbers.length; i++) {
    let arr = answer.split(numbers[i]);
    answer = arr.join(i);
  }

  return Number(answer);
};

console.log(solution("1zerotwozero3"));
```

숫자 string이 들어간 배열을 만들고 순회하셨는데 이 때 `split`을 사용하여 숫자 string을 기준으로 파라미터를 배열로 나누어 변수에 담고 그 사이에 `split`을 사용할 때 기준이 되어 제거되었던 숫자 string의 index를 집어넣어 치환하셨다. 예를 들어 위 코드의 첫 사이클을 나타내보면 `split`이 실행되며 zero를 기준으로 string을 쪼개 `[’1’, ‘two’, ‘3’]` 로 바뀌고 이 배열을 `join`으로 합칠 때 index를 집어넣어 `10two03` 로 합쳐진다. 메서드의 특징을 잘 활용하신 것 같다.

<br>
