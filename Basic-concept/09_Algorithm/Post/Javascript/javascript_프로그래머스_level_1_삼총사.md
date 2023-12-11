# **[Algorithm] 프로그래머스 Level 1 - 삼총사**

2023년 08월 14일

<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/131705

<br>
<br>

## **2. 나의 풀이**

```tsx
const mySolution = (number) => {
  var answer = 0;

  for (let i = 0; i < number.length; i++) {
    for (let j = i + 1; j < number.length; j++) {
      for (let k = j + 1; k < number.length; k++) {
        const sum = number[i] + number[j] + number[k];

        if (sum === 0) answer += 1;
      }
    }
  }

  return answer;
};

console.log(mySolution([-2, 3, 0, 2, -5])); // 2
```

중첩 반복문을 사용하였다. 중복 계산을 막기 위해 내부 반복문들은 자신을 감싸는 반복문의 변수를 기준으로 더하여 초기 값을 설정하였다.

<br>
<br>

## **3. 인기 풀이**

```tsx
const othersSolution = (number) => {
  let answer = 0;

  const combination = (current, start) => {
    if (current.length === 3) {
      answer += current.reduce((acc, cur) => acc + cur, 0) === 0 ? 1 : 0;
      return;
    }

    for (let i = start; i < number.length; i++) {
      combination([...current, number[i]], i + 1);
    }
  };

  combination([], 0);

  return answer;
};

console.log(othersSolution([-2, 3, 0, 2, -5])); // 2
```

재귀 함수를 사용하였다. length가 3이 될 때 해당 사이클의 반복문을 종료하고 다음 사이클로 넘어가는 방식을 활용하였다.

<br>
<br>

## **4. 비교**

나의 풀이와 인기 풀이의 차이점은 구현 방식에 있었다. 나의 풀이는 단순하게 중첩 반복문을 사용하였고 인기 풀이의 경우 재귀 함수를 사용하였다. 인기 풀이를 보며 나의 풀이에 비해 장점이 무엇일까 생각해보았을 때 가독성이 좋아진다는 장점이 있는 것 같았다.

하지만 성능면에서는 나의 풀이와 같이 중첩 반복문이 더 좋은 것으로 알고 있다. 재귀 함수의 경우 함수가 `자기 자신을 호출하는 방식`으로 동작하기 때문에 스택 메모리를 사용하게 되고 호출 스택이 깊어질 경우 스택 오버플로우가 발생할 수 있는 것으로 알고 있다. 아래 이미지를 보았을 때 스택 메모리에 함수 컨텍스트가 계속해서 쌓이는 것을 알 수 있다.

![프로그래머스_Level_1_삼총사_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/4f53a413-4e9f-48f1-8869-97f64e328ade)

반면 중첩 반복문의 경우 스택 메모리를 사용하지 않고 루프를 반복하기 때문에 스택 오버플로우의 위험이 없는 것으로 알고 있다. 그렇기 때문에 데이터 양이 크거나 호출 깊이가 깊은 경우 재귀 함수보다 성능이 우수하다.

![프로그래머스_Level_1_삼총사_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/b8433247-5f26-4968-b3ba-e94231db0e21)

또한 재귀 함수는 함수 호출의 `오버헤드`가 있기 때문에 함수 호출이 빈번하게 일어나는 경우 성능에 영향을 줄 수 있다고 알고 있다. 이에 비해 반복문을 반복 횟수에 비레하여 실행되기 때문에 더 효율적일 수 있다.

<br>
