# **[Algorithm] 프로그래머스 Level 1 - 푸드 파이트 대회**

2023년 08월 22일

<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/134240

<br>
<br>

## **2. 나의 풀이**

```tsx
const mySolution = (food) => {
  var answer = "0";

  for (let i = food.length - 1; i >= 0; i--) {
    if (i === 0) break;

    const repeatCount = Math.floor(food[i] / 2);
    const foodRepeat = String(i).repeat(repeatCount);

    answer = foodRepeat + answer + foodRepeat;
  }

  return answer;
};

console.log(mySolution([1, 3, 4, 6])); // "1223330333221"
```

1. 파라미터로 전달받는 배열 중 물병을 가리키는 index 0의 경우 항상 1의 고정 값을 가지기 때문에 answer의 초기 값을 0으로 설정하였다.
2. 반복문을 돌리는데 배열 index 역순으로 순회하였다. 이유는 string을 편하게 합치기 위해서였다.
3. 우선 플레이어가 먹어야 하는 음식의 개수를 구하기 위해 순회하는 배열의 현재 요소를 2로 나누었다. 이 때 현재 요소가 홀수인 경우 내림 처리를 하여야 하므로 `Math.floor`로 내림 처리 하여 음식의 개수를 구하였다.
4. 음식의 개수만큼 문자열을 생성하기 위해 `repeat` 메소드를 활용하였고 순회하는 현재 index를 음식의 개수만큼 반복하여 문자를 만들었다.
5. 반복되는 문자까지 구한 뒤 현재 answer의 문자를 중간에 배치하여 양 쪽에 반복되는 음식을 붙여 새로운 문자를 생성하였다.

<br>
<br>

## **3. 인기 풀이**

```tsx
const othersSolution = (food) => {
  let res = "";

  for (let i = 1; i < food.length; i++) {
    res += String(i).repeat(Math.floor(food[i] / 2));
  }

  return res + "0" + [...res].reverse().join("");
};

console.log(othersSolution([1, 3, 4, 6])); // "1223330333221"
```

1. 반복문을 돌리는데 물병의 index인 0은 제외하고 1부터 시작하여 반복하였다.
2. 반복문 내부에서 반복되는 음식의 개수를 구하고 `repeat`로 반복하여 한 플레이어가 먹어야 하는 음식의 개수를 문자열로 만들어 `res` 변수에 합산하였다.
3. 출력 시 한 플레이어가 먹어야 하는 음식의 개수에 물병을 나타내는 문자인 0을 더한 뒤 한 플레이어가 먹어야 하는 음식의 개수를 `reverse` 메소드로 뒤집어 합쳐주었다.

<br>
<br>

## **4. 비교**

나의 풀이와 인기 풀이를 비교했을 때 공통점은 음식의 개수를 반복하여 문자열로 변환하는 로직은 완전히 같았다. 차이점은 나의 풀이의 경우 반복문 내부에서 한번에 음식을 누적하여 더해주었고 인기 풀이의 경우 출력 시 한 플레이어가 먹어야 하는 음식을 reverse로 뒤집어 활용하였다. 두 풀이의 큰 차이점은 없었지만 반복문 내부에서 한번 더 연산하는 나의 풀이보다 반복문 내부에서는 반복할 문자만 구한 뒤 reverse를 활용한 인기 풀이가 더 효율적인 로직인 것 같다.

<br>
