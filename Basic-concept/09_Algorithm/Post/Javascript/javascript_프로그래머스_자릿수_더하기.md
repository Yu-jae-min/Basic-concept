# [javascript-algorithm] 프로그래머스 - 자릿수 더하기

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12931" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12931</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let n = 123;

function solution1(n) {
  let answer = 0;
  let nStr = n.toString();

  for (let i = nStr.length - 1; i >= 0; i--) {
    answer += Number(nStr[i]);
  }

  return answer;
}

console.log(solution1(n)); // 6
```

### - 문제해설

> 1.  answer변수에 0 을 할당하고, nStr변수에 매개변수 n을 문자형으로 바꾸어 할당한다.<br>
> 2.  for문을 이용하여 반복하는데 index값이 기준이 되고 length값은 변할 수 있는 값이기 때문에 nStr.length-1로 할당하여 index 끝 자리 수부터 역순으로 더하여준다. 또한 i값이 0보다 크거나 같을 때 까지 반복문을 반복하고 역순으로 반복되기 때문에 증감연산자 i--를 활용한다.<br>
> 3.  answer변수에 문자형으로 변환한 nStr을 순차적으로 더하여 넣어주는데 연산을 하기 위해 Number() 함수를 사용한다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let n = 123;

function solution2(n) {
  return (n + "").split("").reduce((acc, curr) => acc + parseInt(curr), 0);
}

console.log(solution2(n)); // 6
```

### - 문제해설

> 1.  매개변수에 큰따옴표를 더하여 문자형으로 바꿔준다.<br>
> 2.  split()메서드로 문자를 개별로 나누어준다.<br>
> 3.  reduce()메서드를 활용하여 개별로 나누어진 문자형을 누적하여 더하는데 이 때 더하는 값에 parseInt()함수를 넣어주어 숫자형으로 바꾸어 더한다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
let n = 123;

function solution3(n) {
  let sum = 0;

  do {
    sum += n % 10;
    n = Math.floor(n / 10);
  } while (n > 0);

  return sum;
}

console.log(solution3(n)); // 6
```

### - 문제해설

> 1.  sum변수에 0을 할당한다.<br>
> 2.  do-while문을 활용하는데 매개변수가 0보다 클 때 까지 반복한다.<br>
> 3.  sum변수에 n%10을 순차적으로 더해준다. 사이클 순서대로 123의 나머지값 3 -> 12의 나머지값 2 -> 1의 나머지값 1이 더해진다.<br>
> 4.  n변수에 n/10을 할당하는데 소수점을 버리는 Math.floor()함수를 활용하여 할당한다. 사이클 순서대로 12.3의 정수 12 -> 1.2의 정수 1이 할당된다.

<br>

## (3) 참고자료

1. <a href="https://valuefactory.tistory.com/256" target='_blank'>reduce()</a><br>
2. <a href="https://tonks.tistory.com/138" target='_blank'>Math.floor()</a>
