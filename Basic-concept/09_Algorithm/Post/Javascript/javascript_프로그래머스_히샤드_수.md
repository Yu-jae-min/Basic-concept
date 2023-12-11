# [javascript-algorithm] 프로그래머스 - 히샤드 수

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12947" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12947</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let arr = 10;

function solution1(x) {
  let arrString = x + "";
  let arrSum = 0;

  for (let i = 0; i < arrString.length; i++) {
    arrSum += Number(arrString[i]);
  }

  return x % arrSum === 0;
}

console.log(solution1(arr)); // true
```

### - 문제해설

> 1.  arrString변수에 arr변수를 문자열로 바꾸어 할당한다.<br>
> 2.  각각의 숫자를 더하여 할당할 arrSum 변수를 선언하는데 연산을 진행하는 숫자형이어야하기 때문에 0을 할당한다.<br>
> 3.  반복문을 이용하여 문자열로 바꾸어 할당한 arrString변수의 숫자들을 더하여 arrSum에 할당한다. 이 때 문자열에서 숫자형으로 전환한 뒤 더한다.<br>
> 4.  최종출력값은 불리언타입이기 때문에 비교연산자를 활용하여 출력한다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let arr = 10;

function solution2(n) {
  return !(n % (n + "").split("").reduce((a, b) => +a + +b));
}

console.log(solution2(arr)); // true
```

### - 문제해설

> 1.  매개변수 n의 나머지를 구하는 연산을 만든다.<br>
> 2.  매개변수 n을 문자열로 바꿔주기 위해 따옴표를 넣어준다.<br>
> 3.  split() 함수를 사용하여 문자열로 바뀐 n의 값을 자릿 수 마다 나누어준다.<br>
> 4.  reduce() 함수를 활용하여 나누어진 각각의 배열을 합쳐주는데 i와 sum 앞에 +를 붙여주어 숫자형으로 바꾼 후 더해준다.<br>
> 5.  NOT연산자를 넣어 나머지가 없는 0 일때 true, 0 이 아닐 때 false를 출력하도록 한다.

<br>

## (3) 참고자료

1. <a href="https://valuefactory.tistory.com/256" target='_blank'>Array.prototype.reduce()</a>
