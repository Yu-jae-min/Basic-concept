# [Algorithm] 프로그래머스 Level 1 - 덧칠하기

2023년 09월 06일

<br>

## 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/161989

<br>
<br>

## 2. 나의 풀이

```jsx
const mySolution = (n, m, section) => {
  var count = 0;
  let paintedAreas = 0;

  section.forEach((currentAreas) => {
    if (paintedAreas < currentAreas) {
      const paintableAreas = currentAreas + m - 1;

      count++;
      paintedAreas = paintableAreas;
    }
  });

  return count;
};

console.log(mySolution(8, 4, [2, 3, 6])); // 2
```

1. 페인트 칠이 완료된 영역을 할당하기 위한 변수 `paintedAreas`를 생성한다.
2. 페인트가 필요한 영역이 배열로 담긴 section 배열을 `forEach`로 반복하는데 이 때 반복문 내부에서 `if` 조건문을 활용하여 페인트 칠이 완료된 영역이 현재 페인트 칠이 필요한 영역보다 작은 경우 페인트가 필요한 것이기 때문에 확인하였다.
3. if 문 조건에 부합하는 경우 현재 영역에 롤러 길이를 더한 후 1을 빼주어 페인트 칠을 할 영역을 구한 뒤 `paintableAreas` 변수에 할당하고 현재 페인트가 가능한 것이기 때문에 `count` 변수를 증가시킨 뒤 페인트 칠한 영역을 표시하기 위한 변수 `paintedAreas` 에 페인트 칠한 영역을 새로 할당하였다.
4. 최종 페인트 칠한 횟수 `count`를 출력하였다.

<br>
<br>

## 3. 인기 풀이

```jsx
const othersSolution = (n, m, section) => {
  let count = 0;
  const arr = Array.from(Array(n + 1).fill(null));

  section.forEach((el) => {
    arr[el] = 1;
  });

  section.forEach((el) => {
    if (arr[el]) {
      arr.fill(null, el, el + m);
      count++;
    }
  });
  return count;
};

console.log(othersSolution(8, 4, [2, 3, 6])); // 2
```

1. 페인트 칠이 필요한 영역을 표시하기 위해 `arr` 배열을 생성하는데 생성한 배열의 요소 개수는 페인트칠이 필요한 영역에 1을 더한만큼 생성하고 배열 요소를 `fill` 메소드로 페인트 칠이 되었음을 표시하는 null로 채웠다.
2. 페인트 칠이 필요한 영역을 담은 배열 section을 `forEach`로 반복하는데 페인트 칠이 필요한 영역을 표시하기 위한 arr 배열 내부에 페인트 칠이 필요한 영역을 1로 변경해주었다.
3. 다시 한번 페인트 칠이 필요한 영역을 담은 배열 section을 `forEach`로 반복하는데 반복문 내부에서 우선 조건문을 활용하여 페인트 칠이 필요한 영역을 표시한 배열 arr 내부에 페인트 칠이 필요한 영역의 페인트가 아직 칠해지지 않은 경우를 확인하였다.
4. 조건문 조건에 부합하는 경우 페인트 칠한 영역을 null로 바꾸는데 현재 영역부터 현재 영역에 롤러 길이를 더한 영역의 사이를 null로 바꾸고 페인트 칠이 되었으므로 count를 증가시킨다.
5. 최종 페인트 칠한 횟수 `count`를 출력하였다.

<br>
<br>

## 4. 비교

나의 풀이와 인기 풀이의 경우 풀이 속도는 인기 풀이가 아주 미세하게 빨랐다. 또한 가독성은 비슷한 것 같다. 두 풀이의 차이점은 풀이 방식의 차이가 있었다. 나의 풀이의 경우 칠한 영역을 number 타입으로 지정하여 해당 number를 칠한 영역만큼 누적해서 더해주었고 인기 풀이의 경우 페인트 영역을 구분하기 위한 배열을 생성한 뒤 null과 1로 페인트 칠한 영역과 칠해야 하는 영역을 구분한 뒤 fill 메소드를 통해 롤러 길이만큼 페인트를 칠하였다. 풀이 방식은 인기 풀이가 더욱 직관적이고 좋았다고 생각한다. fill 메소드를 적절하게 잘 사용한 것 같다.

<br>
