# [javascript-algorithm] 프로그래머스 - 평균 구하기

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12944" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12944</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let arr = [1, 2, 3, 4];

function solution1(arr) {
  let answer = 0;

  for (let i = 0; i < arr.length; i++) {
    answer += arr[i];
  }

  return answer / arr.length;
}

console.log(solution1(arr)); // 2.5
```

### - 문제해설

> 1.  반복문을 활용하여 answer에 arr배열 요소를 순차적으로 더해준다.<br>
> 2.  출력값은 순차적으로 더해진 변수 answer에 arr.length 값을 나누어 평균을 출력한다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let arr = [1, 2, 3, 4];

function solution2(arr) {
  return arr.reduce((a, b) => a + b) / arr.length;
}

console.log(solution2(arr)); // 2.5
```

### - 문제해설

> 1.  arr.reduce() 메서드를 활용하여 배열의 합을 구한다.<br>
> 2.  배열의 합을 구한 뒤 arr.length 값을 나누어 평균을 구한다.
