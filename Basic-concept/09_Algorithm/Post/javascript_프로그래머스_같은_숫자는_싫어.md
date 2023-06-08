# [javascript-algorithm] 프로그래머스 - 같은 숫자는 싫어

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12906" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12906</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let arr = [1, 1, 3, 3, 0, 1, 1];

function solution1(arr) {
  let answer = [arr[0]];

  for (let i = 1; i < arr.length; i++) {
    if (arr[i - 1] !== arr[i]) {
      answer.push(arr[i]);
    }
  }

  return answer;
}

console.log(solution1(arr)); // [1, 3, 0, 1]
```

### - 문제해설

> 1.  answer변수에 0번째 index배열 요소를 할당한다. 이유는 if문에 -1 이라는 조건이 들어가기 때문이다. 첫번째 배열 요소를 넣은 후 다음 배열 요소와 비교하는 방식의 연산이다.<br>
> 2.  for문으로 배열을 순회한다. i의 초기값은 1로 설정하는데 이유는 if문 조건식 중 -1이 들어가기 때문이다. 예를 들어 -1로 인해 첫번째 사이클에서는 arr[0] !== arr[1]의 조건식이 되는 것이다. 초기값이 0으로 시작하면 음수가 되기 때문에 1로 시작해야한다.<br>
> 3.  조건식을 만족하는 경우 push()메서드로 i번째 배열요소를 answer에 추가한다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let arr = [1, 1, 3, 3, 0, 1, 1];

function solution2(arr) {
  return arr.filter((val, index) => val != arr[index - 1]);
}

console.log(solution2(arr)); // [1, 3, 0, 1]
```

### - 문제해설

> filter()메서드를 활용하다. 처리할 현재 요소의 val 과 arr의 현재 index-1 을 비교하여 true인 경우를 제외하고 배열 요소를 제거하여 새로운 배열을 생성한다.

<br>

## (3) 참고자료

1. <a href="https://aljjabaegi.tistory.com/312" target='_blank'>Array.prototype.filter()</a>
