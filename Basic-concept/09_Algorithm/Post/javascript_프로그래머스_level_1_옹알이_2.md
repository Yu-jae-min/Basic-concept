# **[Algorithm] 프로그래머스 Level 1 - 옹알이 (2)**

2023년 08월 16일

<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/133499

<br>
<br>

## **2. 나의 풀이**

```tsx
const mySolution = (babbling) => {
  var answer = 0;
  const useWords = ["aya", "ye", "woo", "ma"];

  for (let i = 0; i < babbling.length; i++) {
    const repeatRegexp = /(aya|ye|woo|ma)\1+/;

    if (repeatRegexp.test(babbling[i])) continue;

    for (let j = 0; j < useWords.length; j++) {
      if (babbling[i].includes(useWords[j])) {
        babbling[i] = babbling[i].replaceAll(useWords[j], "");
      }
    }

    if (babbling[i] === "") answer++;
  }

  return answer;
};

console.log(mySolution(["ayaye", "uuu", "yeye", "yemawoo", "ayaayaa"])); // 2
```

1. 반복문을 중첩해서 사용하였다. 이 때 첫번째 반복문에서는 정규식을 활용하여 반복되는 문자가 있는지 체크하고 있다면 다음 사이클로 넘어가도록 하였다.
2. 반복되는 문자가 없다면 내부 반복문으로 진입하여 옹알이가 가능한 문자인지 판별하는데 이 때 문자열 중 옹알이가 가능한 단어를 공백으로 치환하였다.
3. 현재 사이클의 단어가 공백인 경우 옹알이가 가능한 것이므로 `answer` 변수를 증가시키고 최종적으로 반복문이 완료된 후 출력하였다.

<br>
<br>

## **3. 인기 풀이**

```tsx
const othersSolution = (babbling) => {
  const regexp1 = /(aya|ye|woo|ma)\1+/;
  const regexp2 = /^(aya|ye|woo|ma)+$/;

  return babbling.reduce(
    (ans, word) => (!regexp1.test(word) && regexp2.test(word) ? ++ans : ans),
    0
  );
};

console.log(othersSolution(["ayaye", "uuu", "yeye", "yemawoo", "ayaayaa"])); // 2
```

1. `regexp1` 변수에 옹알이가 가능한 문자들이 반복되어 사용되는지 체크하는 정규식을 할당한다.
2. `regexp2` 변수에 문자의 시작과 끝이 옹알이가 가능한 문자들로만 이루어져있는지 체크하는 정규식을 할당한다.
3. 파라미터로 넘겨받은 단어 배열을 `reduce` 메소드를 통해 옹알이가 가능한지 체크 후 카운트하는데 이 때 조건은 반복되는 문자가 아닌 경우를 체크하는 `!regexp1.test(word)`, 옹알이가 가능한 문자들로만 이루어져있는지 체크하는 `regexp2.test(word)` 를 모두 통과하는 경우에만 accumulator를 증가시킨다.

<br>
<br>

## **4. 비교**

인기 풀이의 경우 정규식을 활용하여 매우 간결하게 문제를 해결하였다. 하지만 나의 풀이의 경우 반복문을 중첩으로 사용하고 또 정규식도 참조해서 사용했음에도 통과하지 못한 테스트 케이스가 있었다. 아마도 반복문을 통해 순차적으로 옹알이가 가능한 단어들을 제거해나가면서 푸는 방식에서 알 수 없는 오류 케이스가 생겼기 때문으로 예상할 수 있다. 추후에 다시 풀어보아야 할 문제인 것 같다.

<br>
