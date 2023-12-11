# [javascript-algorithm] 프로그래머스 - 수박수박수박수박수박수

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12922" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12922</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let n = 3;

function solution1(n) {
  let answer = "";

  for (let i = 1; i <= n; i++) {
    if (i % 2 === 0) {
      answer += "박";
    } else {
      answer += "수";
    }
  }

  return answer;
}

console.log(solution1(n)); // 수박수
```

### - 문제해설

> 1.  반복문을 이용하여 n보다 작거나 같을 때 까지 반복시킨다.<br>
> 2.  조건문을 활용하여 i를 2로 나눈 나머지가 0일 경우 "박"을 할당하고 아닌 경우 "수"를 할당한다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let n = 3;

const solution2 = (n) => {
  return "수박".repeat(n / 2) + (n % 2 === 1 ? "수" : "");
};

console.log(solution2(n)); // 수박수
```

### - 문제해설

> 1.  '수박'을 repeat()메서드로 n/2만큼 반복시킨다.<br>
> 2.  n이 홀수인 경우 '수'를 추가하고, 아닌 경우 추가하지 않는다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
let n = 3;

const solution3 = (n) => "수박".repeat(n).slice(0, n);

console.log(solution3(n)); // 수박수
```

### - 문제해설

> 1.  '수박'을 repeat()메서드로 n만큼 반복시킨다.<br>
> 2.  반복된 문자열을 slice()메서드로 잘라내는데 0번째부터 시작하여 n번째전까지의 문자를 리턴한다.

<br>

## (3) 참고자료

1. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/slice" target='_blank'>String.prototype.slice()</a><br>
2. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/repeat" target='_blank'>String.prototype.repeat()</a>
