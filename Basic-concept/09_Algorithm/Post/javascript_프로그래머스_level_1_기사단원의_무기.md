# **[Algorithm] 프로그래머스 Level 1 - 기사단원의 무기**

2023년 08월 25일

<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/136798

<br>
<br>

## **2. 나의 풀이**

```jsx
// 첫번째 풀이 : 시간 초과
const mySolution = (number, limit, power) => {
  var answer = 0;
  const divisorArray = [];

  for (let i = 1; i <= number; i++) {
    let divisorCount = 0;

    for (let j = 1; j <= i; j++) if (i % j === 0) divisorCount++;

    divisorArray.push(divisorCount);
  }

  divisorArray.forEach((divisor) => {
    if (divisor > limit) return (answer += power);

    return (answer += divisor);
  });

  return answer;
};

console.log(mySolution(5, 3, 2)); // 10
```

```jsx
// 두번째 풀이 : 시간 초과 해결
const mySolution = (number, limit, power) => {
  var answer = 0;
  const divisorArray = [];

  for (let i = 1; i <= number; i++) {
    let divisorCount = 1; // 개선된 부분

    for (let j = 1; j <= i / 2; j++) if (i % j === 0) divisorCount++; // 개선된 부분

    divisorArray.push(divisorCount);
  }

  divisorArray.forEach((divisor) => {
    if (divisor > limit) return (answer += power);

    return (answer += divisor);
  });

  return answer;
};

console.log(mySolution(5, 3, 2)); // 10
```

1. 약수 배열을 담기 위한 `divisorArray` 변수를 생성하였다.

2. `for 문`을 통해 반복하는데 이 때 약수의 시작 값은 1 이므로 초기 값을 1 로 할당하고 중첩 반복문을 통해 현재 수 `i`까지 차례대로 `j`가 증가하며 약수인지 평가한 후 약수인 경우 블록 레벨 스코프를 가진 `divisorCount`가 증가하도록 하였다. 그 후 내부 반복문 종료 시 카운트 된 `divisorCount` 값을 약수 배열 `divisorArray`에 `push` 해주었다.

   > 첫번째 풀이의 경우 `시간 초과가 발생`했다. 이유는 해당 풀이의 경우 중첩 반복문을 사용하여 시간 복잡도가 `O(n^2)`인데 이 때 number가 커지게 되면 그에 따라 시간 복잡도가 크게 증가하여 시간 초과가 발생한 것이다. 이 문제를 해결 하기 위해 약수는 본인을 제외하고 본인의 절반 값보다 클 수 없다는 것을 활용하여 내부 중첩문의 반복 조건을 절반으로 줄였다. 그 후 블록 레벨 스코프를 가지는 `divisorCount` 변수에 초기 값을 본인의 약수가 본인인 경우를 포함하기 위해 0에서 1로 변경하였다.

3. 약수를 모두 구한 뒤 해당 배열을 `forEach`로 반복하였는데 이 때 반복문 내부에서는 해당 약수가 허용 된 최대 값인 limit를 초과하는지 확인 한 후 초과한다면 power, 초과하지 않는다면 현재 약수 값을 answer에 누적해서 더하였다. 그 후 answer을 출력하였다.

<br>
<br>

## **3. 인기 풀이**

```jsx
const othersSolution = (number, limit, power) => {
  var answer = 0;

  for (let n = 1; n <= number; n++) {
    let count = 0;

    for (let j = 1; j * j <= n; j++) {
      if (j * j == n) count++;
      else if (n % j == 0) count += 2;
    }

    if (count > limit) count = power;

    answer += count;
  }

  return answer;
};

console.log(othersSolution(5, 3, 2)); // 10
```

1. `for 문`을 통해 반복하는데 이 때 약수의 시작 값은 1 이므로 초기 값을 1 로 할당하였다.

2. 내부 반복문에서 반복 조건은 `j * j`과 같이 제곱근을 활용하였다. 제곱근을 활용한 이유는 아마도 나와 같이 절반의 값만 계산하도록 하기 위함인 것 같다. 그 후 반복문 내부에서 제곱근을 활용하여 카운트를 증가시켰다.

   > 예를 들어 100의 제곱근을 구할 때 10까지만 구하는데 이 때 구해지는 값은 10의 약수인 1, 2, 5, 10이지만 이건 [1, 100], [2, 25], [5, 20], [10, 10]인 100의 모든 약수를 뜻한다. 즉 1을 구한다면 100을 함께 구하는 것과 같은 의미이고 2를 구한다면 25, 5를 구한다면 20을 함께 구하게 되는 것이다. 그렇기 때문에 +2를 해주는 것이고 10을 구할 땐 [10,10] 중복이기 때문에 +1을 해주는 것이다.

3. 반복문 내부에서 카운트가 완료 된 후 해당 값이 limit를 넘어가는지 확인한 후 넘어가는 경우 power를 재할당하고 아닌 경우 카운트 된 값을 그대로 활용하여 answer에 누적해서 더하였다. 그 후 최종 값을 출력하였다.

<br>
<br>

## **4. 비교**

우선 나의 풀이와 인기 풀이의 가장 큰 차이점은 처리 속도면에서 차이가 났다. 인기 풀이의 경우 제곱근을 활용하여 약수의 개수를 구하는 방식을 활용해 반복되는 횟수를 현저하게 줄였다. 만약 파라미터로 전달되는 number가 100일 때 중첩 반복문 중 내부 반복문이 실행되는 횟수를 카운트해보면 나의 풀이의 경우 2500, 인기 풀이의 경우 625라는 숫자가 나왔다. 이 값은 number가 커지면 커질수록 차이가 발생하였다. 여기서 느낀점은 알고리즘에 있어 수학적인 능력은 정말 크게 필요하다고 느꼈다. 나의 경우 단순히 약수는 자기 자신의 수를 제외하고 자기 자신의 절반 값을 초과할 수 없다라는 점만 참고하여 코드를 작성하였다. 또한 하단에 불필요한 forEach 문도 추가되었다. forEach문을 제거하고 위 for 중첩 반복문에서 divisorCount 값을 divisorArray에 push 하기전에 해당 값이 limit를 초과하는지 체크하여 push 할 수 있었을 것 같다. 이번 문제에서 나의 풀이는 여러모로 아쉬운 코드이다.

<br>
