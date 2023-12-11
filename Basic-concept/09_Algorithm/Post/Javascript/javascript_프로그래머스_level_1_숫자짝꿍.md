# **[Algorithm] 프로그래머스 Level 1 - 숫자 짝꿍**

2023년 07월 24일

<br>

## **1. 문제**

<a href="https://school.programmers.co.kr/learn/courses/30/lessons/131128" target='_blank'>https://school.programmers.co.kr/learn/courses/30/lessons/131128</a>

<br>
<br>

## **2. 풀이**

### **2-1. 풀이1**

```jsx
const x = "5525";
const y = "1255";

const solution = (x, y) => {
  const partnerList = [];
  const arrX = x.split("");
  const arrY = y.split("");

  for (let i = 0; i < arrX.length; i++) {
    for (let j = 0; j < arrY.length; j++) {
      if (arrX[i] === arrY[j]) {
        partnerList.push(arrY[j]);

        arrX.splice(i, 1);
        i--;

        arrY.splice(j, 1);
        j--;

        break;
      }
    }
  }

  const maxValue = partnerList.sort((a, b) => b - a).join("");
  const changedFormat = Number(maxValue).toString();
  const result = partnerList.length > 0 ? changedFormat : "-1";

  return result;
};

console.log(solution2(x, y));
```

X와 Y를 중첩으로 순회하며 값이 같은 경우 `partnerList` 배열에 해당 값을 넣었다.
그 후 해당 값을 제거하고 순회 값인 i와 j를 1씩 감소시켰다.
그리고 break를 사용하여 for문의 다음 사이클로 넘어갈 수 있도록 하였다.

처음 테스트 결과는 정상적으로 작동하였으나 전체 테스트 케이스에서 걸려버렸다.
문제를 자세히보니 정수가 300만개 이상까지 허용하고 있었다. 그렇기 때문에 시간 초과가 발생했다.
아마도 중첩 for문 사용하여 시간 초과가 발생했던 것 같다.

<br>

### **2-2. 풀이2**

```jsx
const x = "5525";
const y = "1255";

const solution = (x, y) => {
  let answer = "";
  const arrX = x.split("").sort((a, b) => b - a);
  const arrY = y.split("");
  const count = {};

  arrY.forEach((y) => {
    if (count[y] === undefined) {
      count[y] = 1;
    } else {
      count[y]++;
    }
  });

  arrX.forEach((x) => {
    if (count[x] !== undefined && count[x] !== 0) {
      count[x]--;
      answer = answer.concat(x);
    }
  });

  if (answer.length === 0) return "-1";
  if (answer[0] === "0") return "0";

  return answer;
};

console.log(solution(x, y));
```

우선 `arrY`를 순회하여 객체의 key, value 페어로 1씩 증가시키며 저장하였다.

그 후 `arrX`를 순회하며 해당 값이 존재하면 해당 값을 기준 문자열인 `answer`에 합치고 카운트를 1씩 감소시켰다.

마지막으로 결과 값 반환을 위해 `answer` 길이가 0인 경우(짝꿍이 존재하지 않는 경우) -1, 짝꿍이 존재하지만 그 값이 0인 경우, 그리고 나머지 경우로 나누어 값을 반환하였다.

해당 풀이는 다른 개발자분의 코드를 참고로 작성하였다. 처음에 배열로 풀이1과 같이 배열로 해결하는 방식만 생각났었다. 하지만 객체로 처리하여 카운트시키니 연산이 훨씬 줄어드는 것을 알 수 있었다.

<br>
