# [javascript-algorithm] 프로그래머스 - 제일 작은 수 제거하기

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12935" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12935</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let arr = [4, 3, 2, 1];

function solution(arr) {
  var answer = [];

  if (arr.length <= 1) {
    return [-1];
  } else {
    arr.splice(arr.indexOf(Math.min(arr)), 1);
    answer = arr;
  }

  return answer;
}

console.log(solution(arr)); // [4, 3, 2]
```

### - 문제해설

> 1.  answer 에 빈 배열을 추가한다.<br>
> 2.  if문을 활용하여 첫번째 조건을 만든다. arr 배열의 원소가 1개이거나 1개보다 작을 때 -1 값을 반환한다.<br>
> 3.  if문을 활용하여 두번째 조건을 만든다. 원소가 1개를 초과할 때 arr.splice()로 배열을 수정한다. arr.indexOf()를 통해 특정문자열을 찾아서 반환하는데, 주어진 조건인 최소값을 찾아야하기 때문에 Math.min(arr) 로 최소값을 찾는다. 이 최소값이 arr.splice()의 첫번째 파라미터 값이 되고 두번째 파라미터 값은 1 이다. 그러므로 첫번째 파라미터 값부터 1개를 삭제하기 때문에 최소값이 삭제된다.<br>
> 4.  마지막으로 빈 배열인 answer 에 최소값을 삭제하여 재할당한 배열 arr 을 넣어준다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let arr = [4, 3, 2, 1];

const solution = (arr) => {
  arr.splice(arr.indexOf(Math.min(...arr)), 1);
  return arr.length ? arr : [-1];
};

console.log(solution(arr)); // [4, 3, 2]
```

### - 문제해설

> 1.  arr.splice를 활용하여 arr배열을 수정한다.<br>
> 2.  splice의 첫번째 파라미터값은 시작위치, 두번째 파라미터값은 제거할 갯수이므로 첫번째 파라미터값은 최소값, 두번째 파라미터값은 최소값을 삭제하기 위해 1을 넣어주어야한다. 최소값을 추출하기 위해 indexOf를 활용하여 최소값 문자열을 탐색하는데 파라미터값으로 배열의 최소값을 넣어 arr배열 안에 최소값을 추출한다. 이 때 Math함수의 파라미터값은 배열이 아닌 숫자형을 파라미터값으로 가져야한다. 이럴 때 전개연산자인 ...을 활용하면 arr의 배열값을 그대로 옮길 수 있다.<br>
>
> - 전개연산자를 사용하지 않으면 Math.min(arr)의 반환값은 NaN 이 된다.<br>
>
> 3.  리턴값을 삼항연산자를 활용하여 arr과 -1을 리턴한다. 최종 리턴되는 배열 원소 갯수가 0개인 경우는 렝스값이 0이기 때문에 false에 [-1]을 넣어준다. 또한 0개가 아닌 경우는 배열 값을 리턴해야하므로 true에 arr배열을 넣어준다.<br>
>
> - false로 간주되는 경우 : undefined , null , 0 , -0 , NaN , ""

<br>

## (3) 참고자료

1. <a href="https://mine-it-record.tistory.com/352" target='_blank'>Array.prototype.splice()</a><br>
2. <a href="https://hianna.tistory.com/379" target='_blank'>String.prototype.indexOf()</a><br>
3. <a href="https://yuddomack.tistory.com/entry/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EB%AC%B8%EB%B2%95-%EB%B9%84%EA%B5%AC%EC%A1%B0%ED%99%94-%ED%95%A0%EB%8B%B9" target='_blank'>...(전개연산자)</a>
