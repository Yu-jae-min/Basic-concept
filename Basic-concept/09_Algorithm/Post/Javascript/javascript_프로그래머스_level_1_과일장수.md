# **[Algorithm] 프로그래머스 Level 1 - 과일 장수**

2023년 08월 23일

<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/135808

<br>
<br>

## **2. 나의 풀이**

```tsx
const mySolution = (k, m, score) => {
  var answer = 0;

  const appleBox = [];
  const appleRemainingCount = Math.floor(score.length % m) * -1 || score.length;
  const applePoint = score.sort().reverse().slice(0, appleRemainingCount);

  applePoint.forEach((apple) => {
    appleBox.push(apple);

    if (appleBox.length === m) {
      answer += appleBox[m - 1] * m;
      appleBox.splice(0);
    }
  });

  return answer;
};

console.log(mySolution(3, 4, [1, 2, 3, 1, 2, 3, 1])); // 8
```

1. stack으로 과일을 담아서 합산할 것이기 때문에 빈 배열 appleBox을 생성하였다.
2. 상자에 담지 못하는 사과는 버려야 하기 때문에 나머지 값을 구해 `appleRemainingCount` 변수에 할당하였다. 이 때 slice 메소드를 활용하여 배열 뒤에서 부터 자르기 때문에 음수로 변환하고자 음수를 곱하였고 만약 나머지 값이 없다면 모든 배열을 그대로 유지해야 하기 때문에 score.length를 반환하였다.
3. `applePoint` 변수에 상자에 담길 과일 배열을 담았다. 이 때 sort를 통해 오름차순 정렬한 뒤 reverse로 내림차순으로 바꿨다. 그 후 점수가 낮은 과일 중 나머지 값에 해당되는 과일들을 slice 메소드로 잘라주었다.
4. applePoint를 forEach를 통해 반복하였는데 이 때 stack을 쌓기 위해 생성한 빈 배열 appleBox에 순차적으로 push 해주었다. 그 후 appleBox에 길이가 한 상자에 담기는 사과의 수 m과 같아지는 경우 해당 배열의 끝, 즉 내림차순 정렬되어있기 때문에 해당 배열의 최소 값을 상자에 담기는 사과 수 m과 곱하여 상자의 가격을 구한 뒤 answer 변수에 누적하여 더했다. 그 후 stack을 비워주기 위해 splice 메소드로 appleBox 배열을 비워주었다.

<br>
<br>

## **3. 인기 풀이**

```tsx
const othersSolution = (k, m, score) => {
  return (
    score
      .sort()
      .filter((_, i) => !((score.length - i) % m))
      .reduce((a, v) => a + v, 0) * m
  );
};

console.log(othersSolution(3, 4, [1, 2, 3, 1, 2, 3, 1])); // 8
```

1. `sort`를 사용하여 과일 점수를 오름차순으로 정렬하였다.
2. `filter`를 사용하는데 내부에서 과일 점수 배열의 길이를 현재 과일 점수 index로 뺀 뒤 나머지 값을 구하고 이 값을 boolean으로 판별하였다. 즉 sort 후 각 과일 상자의 최소 값을 구하기 위해 m 번째에서 잘리는 값만 가져온 것이다. m 번째에서 잘리는 경우 `(score.length - i) % m` 의 값이 0이 나오므로 이 값을 ! 연산자를 통해 뒤집어 boolean으로 판별한 것이다.
3. filter를 통해 최소 값들을 담은 배열을 만들어낸 뒤 reduce로 합치고 과일 상자 갯수를 곱해준다.

<br>
<br>

## **4. 비교**

나의 풀이에 비해 인기 풀이는 코드의 길이나 사용한 메소드가 현저히 적었다. 인기 풀이의 경우 filter 메소드를 통해 최소 값들을 담은 배열을 한번에 생성하여 이 배열을 합산한 뒤 상자를 곱해주는 방식으로 해결하였다. 하지만 나의 경우 나머지 값을 우선 잘라낸 뒤 해당 배열들을 stack으로 푸시하며 순차적으로 처리하였다. 추가적인 작업들을 통해 코드 길이가 길어질 수 밖에 없었던 것 같다. 인기 풀이와 같이 간결하게 해결하는 사고를 길러야겠다.

<br>
