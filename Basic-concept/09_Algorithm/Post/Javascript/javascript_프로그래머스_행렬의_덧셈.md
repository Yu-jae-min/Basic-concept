# [javascript-algorithm] 프로그래머스 - 행렬의 덧셈

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12950" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12950</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
const arr1 = [
  [1, 2],
  [2, 3],
];
const arr2 = [
  [3, 4],
  [5, 6],
];

function solution(arr1, arr2) {
  let answer = [[]];
  for (let i = 0; i < arr1.length; i++) {
    answer[i] = [];
    for (let j = 0; j < arr1[i].length; j++) {
      answer[i].push(arr1[i][j] + arr2[i][j]);
    }
  }
  return answer;
}

console.log(solution(arr1, arr2)); // [[4,6],[7,9]]
```

### - 문제해설

> 1.  배열안의 원소가 배열이기때문에 중첩 for문을 활용한다.<br>
> 2.  answer 변수안에 배열의 원소를 빈 배열로 할당한다. 문제 중 배열이 `[[]]`로 선언되어있기 때문에 빈 배열을 할당해주어야 오류를 피할 수 있다. 아래 연산에 들어갈 배열 원소의 배열들을 push로 여기에 추가하는 것이다.<br>
> 3.  중첩 for문안에 push와 연산을 활용하여 연산된 값을 넣어준다. push되는 위치가 answer이 아닌 answer[i]인 이유는 출력값이 각각의 배열로 나뉘어 있어야 하기 때문이다. answer[i]가 아닌 answer로 더한 값을 전달할 시 출력값은 [4,6,7,9]이 된다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
const arr1 = [
  [1, 2],
  [2, 3],
];
const arr2 = [
  [3, 4],
  [5, 6],
];

function solution(arr1, arr2) {
  return arr1.map((arr, i) => arr.map((n, j) => n + arr2[i][j]));
}

console.log(solution(arr1, arr2)); // [[4,6],[7,9]]
```

### - 문제해설

> 1.  arr1 의 배열을 수정하기 위해 arr1.map()을 사용한다. arr1.map(arr, i)의 요소값과 인덱스값이 들어가는데 요소값인 arr은 `[[1,2],[2,3]]`를 가르킨다.<br>
> 2.  두번째로 arr1.map(arr, i)의 인자값 arr에 map을 중첩으로 사용한다. 이유는 배열안의 배열을 연산해야하기때문에 중첩으로 사용 후 연산값을 넣어준다. arr.map과 같이 넣어주는데 여기서 arr이 `[[1,2],[2,3]]`의 배열 중 [1,2]혹은[2,3]을 가르키게 된다.<br>
> 3.  arr.map을 가르키는 요소값 n에 arr2[i][j]를 더해준다.

<br>

## (3) 참고자료

1. <a href="https://hashcode.co.kr/questions/7544/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EC%97%90%EC%84%9C-%ED%99%94%EC%82%B4%ED%91%9C%EA%B0%80-2%EB%B2%88-%EC%97%B0%EC%86%8D%EC%9C%BC%EB%A1%9C-%EB%82%98%EC%98%A4%EB%8A%94-%EA%B2%BD%EC%9A%B0%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C-%ED%95%B4%EC%84%9D%ED%95%B4%EC%95%BC%ED%95%98%EB%82%98%EC%9A%94" target='_blank'>화살표 함수 중첩 사용</a><br>
2. <a href="https://siyoon210.tistory.com/162" target='_blank'>자바스크립트의 중첩함수</a>
