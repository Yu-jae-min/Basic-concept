# [Algorithm] 프로그래머스 Level 1 - 대충 만든 자판

2023년 09월 04일

<br>

## 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/160586

<br>
<br>

## 2. 나의 풀이

```jsx
const mySolution = (keymap, targets) => {
  var answer = new Array(targets.length).fill(0);

  for (let i = 0; i < targets.length; i++) {
    const splitTarget = [...targets[i]];

    for (let j = 0; j < splitTarget.length; j++) {
      const indexArray = keymap
        .map((key) => [...key].indexOf(splitTarget[j]) + 1)
        .filter((idx) => !!idx);

      if (!indexArray.length) {
        answer[i] = -1;
        break;
      } else {
        answer[i] = answer[i] + Math.min(...indexArray);
      }
    }
  }

  return answer;
};

console.log(mySolution(["ABACD", "BCEFD"], ["ABCD", "AABB"])); // [9, 4]
```

1. 파라미터로 전달받은 `targets` 문자열을 입력하기 위해 눌러야 할 최소 키 수를 카운트 하기 위해 `Array 생성자`를 통해 배열을 생성하는데 배열 요소의 길이는 타겟 문자열의 길이 만큼 생성하고 `fill`을 통해 해당 배열을 0으로 채웠다.
2. `for문`을 통해 반복하는데 이 때 반복되는 기준은 targets 문자열이 담긴 배열의 길이만큼 반복한다. 반복문 내부에서는 해당 배열에 담긴 문자열을 `spread 문법`을 통해 각 요소로 나누어 `splitTarget` 변수에 할당하였다. (ex `[“ABCD”]` ⇒ `[”A”, “B”, “C”, “D”`])
3. 문자열을 각 요소로 나눈 `splitTarget` 변수를 기준으로 `for문`을 중첩해서 사용하였다. 이 때 중첩 반복문 내부에서는 map 메소드를 활용하여 키 입력 규칙이 담긴 문자열을 요소로 갖는 배열 `keymap`을 변환하였는데 변환되는 값은 현재 입력해야 할 문자열의 index에 입력해야 하는 횟수이므로 1을 더한 값으로 변환하였다. 그 후 `indexArray` 변수에 할당하였다.
4. 현재 문자열의 키 입력 횟수가 담긴 `indexArray` 배열 filter 메소드를 활용하여 필터 처리 하였는데 필터 기준은 값이 존재하는지를 기준으로 필터하였다. 즉 키 입력 규칙 중 현재 키를 입력할 수 없는 경우를 필터 처리 한 것이다.
5. `if문`을 통해 현재 입력해야하는 문자열의 키 입력 횟수가 담긴 배열 indexArray의 요소가 없는 경우 `-1`을 반환하도록 하였고 요소가 있는 경우 최저 횟수를 반환하기 위해 `Math.min`을 활용하여 최저 횟수를 구하였다. 그 후 순회중인 현재 index와 동일한 위치에 answer 배열 내부에 누적하여 더해주었다.

<br>
<br>

## 3. 인기 풀이

```jsx
const othersSolution = (keymap, targets) => {
  const answer = [];
  const map = {};

  for (const items of keymap) {
    items
      .split("")
      .map(
        (item, index) =>
          (map[item] = map[item] < index + 1 ? map[item] : index + 1)
      );
  }

  for (const items of targets) {
    answer.push(
      items.split("").reduce((cur, item) => (cur += map[item]), 0) || -1
    );
  }

  return answer;
};

console.log(othersSolution(["ABACD", "BCEFD"], ["ABCD", "AABB"])); // [9, 4]
```

1. 입력할 수 있는 키의 최저 횟수가 담긴 객체 `map`를 생성하였다.
2. `for of문`으로 반복하는데 이 때 반복되는 기준은 키 입력 규칙이 담긴 `keymap`을 기준으로 반복하였고 반복문 내부에서 `split` 메소드를 통해 키 입력 규칙 문자열을 각 문자로 나누었다. 그 후 해당 배열을 `map` 메소드를 사용하여 순회하였는데 입력할 수 있는 키의 최저 횟수가 담긴 객체 map 내부에 현재 문자열 요소와 같은 key를 가진 프로퍼티의 value가 현재 문자열 요소의 입력하기 위해 눌러야 하는 횟수 index + 1 값보다 작은 경우 기존 프로퍼티를 그대로 유지하고 아닌 경우 최저 횟수를 새로 할당하였다.
3. `for of문`으로 반복하는데 이 때 반복되는 기준은 입력해야하는 문자열을 요소로 갖는 배열 `targets`을 기준으로 반복하였고 반복문 내부에서 출력하기 위한 배열 `answer`에 `push` 메소드로 출력하기 위한 요소를 추가해주었는데 추가해주는 값은 현재 눌러야 하는 문자열 요소를 `split` 메소드로 잘라 각 배열 요소로 나눈 뒤 `reduce` 메소드를 활용하여 누산 값을 활용해 추가해주었다. 이 때 reduce 내부에서는 현재 누산 값 cur에 키 입력을 위해 필요한 횟수가 담긴 map 객체 프로퍼티 값을 활용하여 누적해서 더해주었다. 이 때 현재 누산 값이 없다면 `-1`이 answer 배열로 추가되도록 `OR 연산자`를 활용하였다.

<br>
<br>

## 4. 비교

나의 풀이와 인기 풀이의 속도 차이는 크게 나지 않았다. 하지만 가독성은 딱 봐도 인기 풀이가 월등하게 좋았던 것 같다. 나의 경우 중첩 반복문을 사용하여 한 번에 처리하였는데 한 번에 처리하기 위한 일련의 과정들이 너무나 복잡해보였다. 반면 인기 풀이의 경우 동일한 반복문 for of문을 나누어 사용하며 가독성을 확보한 것 같다. 또한 반복문 내부에서 처리하는 값들은 관심사를 정확히 나누었다. 첫번째 반복문에서 키 입력을 위해 필요한 최저 횟수가 담긴 객체를 생성하였고 두번째 반복문에서 최저 횟수가 담긴 객체 프로퍼티의 value를 활용하여 누산한 뒤 출력해야하는 변수에 추가해주었다. 정말 깔끔한 코드다.

내 코드보다 너무 깔끔하고 잘 짠 코드이지만 아쉬워보이는 점이 있다면 우선 for of문 내부에서 입력할 수 있는 키 요소를 갖는 배열을 순회할 때 map 메소드를 사용했다는 점이다. map 메소드는 새로운 배열을 생성하는데 이 때 해당 로직에서는 새로운 배열을 생성할 필요가 없기 때문에 메모리 낭비가 발생하게 된다. 그렇기 때문에 forEach 메소드로 바꾸는 게 더 좋을 것 같다. 또한 변수 활용이 적극적이지 않았던 점도 아쉬운 것 같다. index + 1과 같은 동일하게 사용되는 부분이 있는 경우 변수를 활용했으면 좋았을 것 같고 push 메소드 내부에서도 OR 연산자를 통해 값을 할당할 때 해당 값들을 변수를 사용해서 각각 처리 후 OR 연산자의 값으로 할당했으면 더욱 가독성이 좋아질 것 같다고 생각했다.

<br>
