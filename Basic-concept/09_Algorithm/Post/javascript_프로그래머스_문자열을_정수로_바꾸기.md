# [javascript-algorithm] 프로그래머스 - 문자열을 정수로 바꾸기

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12925" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12925</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let str = "-1234";

function solution1(str) {
  return Number(str);
}

console.log(solution1(str)); // -1234
```

### - 문제해설

> Number()함수를 이용하여 숫자형으로 변환한다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let str = "-1234";

function solution2(str) {
  return parseInt(str);
}

console.log(solution2(str)); // -1234
```

### - 문제해설

> parseInt()함수를 이용하여 숫자형으로 변환한다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
let str = "-1234";

function solution3(str) {
  return str / 1;
}

console.log(solution3(str)); // -1234
```

### - 문제해설

> 사칙연산 \*,/를 이용하여 자동형변환한다.

<br>

## (2) 문제풀이 및 해설 4

### - 문제풀이

```javascript
let str = "-1234";

function solution4(str) {
  return +str;
}

console.log(solution4(str)); // -1234
```

### - 문제해설

> 사칙연산 +를 이용하여 자동형변환한다.

<br>

## (3) 참고자료

1. <a href="https://programmingsummaries.tistory.com/355" target='_blank'>문자를 숫자로 바꾸는 가장 좋은 방법</a><br>
1. <a href="https://medium.com/gdana/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EC%9D%98-%ED%98%95%EB%B3%80%ED%99%98%EC%9D%80-%EB%91%90%EA%B0%80%EC%A7%80%EB%8B%A4-b46875be4a88" target='_blank'>암시적변환과 명시적변환</a><br>
1. <a href="https://velog.io/@yejinh/Javascript-%ED%98%95%EB%B3%80%ED%99%98" target='_blank'>Javascript 형변환</a>
