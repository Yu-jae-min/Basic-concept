# **[Algorithm] 프로그래머스 Level 1 - 가장 가까운 같은 글자**

2023년 08월 28일

<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/142086

<br>
<br>

## **2. 나의 풀이**

```jsx
const mySolution = (s) => {
  const answer = s.split("").map((str, idx, arr) => {
    const sliceArr = arr.slice(0, idx);

    if (sliceArr.includes(str)) {
      return idx - sliceArr.lastIndexOf(str);
    }

    return -1;
  });

  return answer;
};

console.log(mySolution("banana")); // [-1, -1, -1, 2, 2, 2]
```

1. 파라미터로 받은 문자열을 `split` 메소드로 잘라 배열로 만든 뒤 map으로 돌려 요소를 변환시켰다. 이 때 map 내부에서는 우선 기준이 되는 배열 arr을 `slice`로 자르는데 배열의 처음인 0부터 현재 idx까지 자르도록 하여 현재 요소 이전까지의 요소가 담긴 배열 `sliceArr`을 생성하였다.
2. 현재 요소 이전까지의 요소가 담긴 배열 `sliceArr`을 이용하여 해당 배열에 현재 요소가 포함되어 있는지 조건문을 통해 체크하였다. 만약 현재 요소가 포함되어 있지 않다면 `-1`을 반환하도록 하였고 포함되어 있다면 현재 인덱스에 현재 요소 이전까지의 요소가 담긴 배열 `sliceArr`에서 현재 요소와 같은 요소의 마지막 인덱스를 뺀 값을 출력하도록 하였다.

<br>
<br>

## **3. 인기 풀이**

```jsx
const othersSolution = (s) => {
  const hash = {};

  return [...s].map((v, i) => {
    let result = hash[v] !== undefined ? i - hash[v] : -1;
    hash[v] = i;
    return result;
  });
};

console.log(othersSolution("banana")); // [-1, -1, -1, 2, 2, 2]
```

1. 숫자를 카운트하기 위해 `hash` 객체를 생성하였다.
2. 전달 받은 문자열 s를 스프레드 문법을 통해 배열로 만든 뒤 map을 돌려 요소를 변환시켰다. 이 때 map s내부에서 생성해놓은 `hash` 객체 내부에 현재 요소가 존재하는지 판별한 뒤 없다면 `-1`, 있다면 현재 요소의 인덱스에서 `hash` 객체 내부에 현재 요소의 value를 뺀 값을 result 변수에 할당하였다.
3. 그 후 `hash` 객체 내부 현재 요소의 value을 현재 요소의 index로 할당하였다.
4. 최종적으로 조건문을 통해 반환 된 값을 출력하였다.

<br>
<br>

## **4. 비교**

나의 풀이와 인기 풀이의 경우 문자열을 배열로 변환한 뒤 map을 통해 배열 요소를 변환시켰다. 이 때 나의 풀이의 경우 slice 메소드를 통해 비교할 배열을 생성하였고 해당 배열을 조건문의 조건으로 활용하여 포함 여부를 체크하여 포함 여부에 맞는 값을 반환하도록 하였다. 반면 인기 풀이의 경우 map 외부에 객체를 생성해놓고 해당 객체에 현재 문자의 index를 저장하는 방식을 통해 문제를 해결하였다. 두 풀이의 속도를 극단적인 상황에서 비교해보았다. 만약 전달되는 파라미터의 문자열 길이가 10000자인 경우 속도 차이는 최소 5배에서 최대 8배 정도 인기 풀이의 속도가 더 빨랐다. 그래서 속도 차이가 난 이유는 map 내부에서 사용 된 slice 때문에 속도 차이가 발생했다. map만 사용했을 때는 동일하게 `O(n)`의 시간 복잡도를 가지는데 내부에서 slice 메소드를 사용하게 되면서 시간 복잡도가 `O(n^2)`로 늘어났기 때문에 발생한 차이였다.

<br>
