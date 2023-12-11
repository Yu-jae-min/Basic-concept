# [javascript-algorithm] 프로그래머스 - 부족한 금액 계산하기

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/82612" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/82612</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let price = 3;
let money = 20;
let count = 4;

function solution1(price, money, count) {
  let answer = 0;

  for (let i = 1; i <= count; i++) answer += price * i;

  return answer > money ? answer - money : 0;
}

console.log(solution1(price, money, count)); // 10
```

### - 문제해설

> 1.  for문을 이용하여 i가 conut보다 작거나 같을 경우 반복하여 실행한다.<br>
> 2.  변수 answer에 회차당 증가하는 price \* i값을 누적하여 더해준다.<br>
> 3.  삼항연산자를 활용하여 필요금액 answer이 소지금액 money보다 클 경우 필요금액-소지금액을 출력하고 부족하지 않은 경우 0을 출력한다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let price = 3;
let money = 20;
let count = 4;

function solution2(price, money, count) {
  const tmp = (price * count * (count + 1)) / 2 - money;
  return tmp > 0 ? tmp : 0;
}

console.log(solution2(price, money, count)); // 10
```

### - 문제해설

> 1.  등차수열의 합(1 ~ x까지의 합 = n \* (n + 1) / 2)을 활용한다.<br>
> 2.  이 때 price배만큼 곱해줘야하므로 price를 앞에 곱해준다.<br>
> 3.  최종적으로 price _ count _ (count + 1) / 2 까지가 필요금액이 되고 money를 빼주어 필요금액과 소지금액의 차이를 구한다.<br>
> 4.  삼항연산자를 활용하여 필요금액-소지금액을 담아둔 변수 tmp의 값이 0보다 클 경우 tmp를 리턴하고 작을 경우 0을 리턴한다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
let price = 3;
let money = 20;
let count = 4;

const solution3 = (...list) =>
  Math.max((list[0] * list[2] * ++list[2]) / 2 - list[1], 0);

console.log(solution3(price, money, count)); // 10
```

### - 문제해설

> 1.  화살표 함수를 생성하는데 매개변수는 Rest파라미터를 활용하여 매개변수 목록을 넣는다.<br>
> 2.  등차수열의 합(1 ~ x까지의 합 = n \* (n + 1) / 2)을 활용한다.<br>
> 3.  ...\_ 는 함수에 들어오는 매개변수의 목록을 의미하고 함수 몸체에서 \_\[0]은 price, \_\[1]은 money, \_\[2]는 conut이다. 즉 price _ count _ ++count / 2 - money가 되는 것이다.<br>
> 4.  Math.max를 활용하여 위 식의 결과, 0을 배치하여 두 개의 숫자 중 더 큰 숫자를 반환하도록 한다.

<br>

## (3) 참고자료

1. <a href="https://m.blog.naver.com/seekhim/222280134895" target='_blank'>등차수열의 합(가우스 공식)</a><br>
2. <a href="https://curryyou.tistory.com/236" target='_blank'>Rest파라미터(...)</a><br>
3. <a href="https://medium.com/@shlee1353/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-spread%EC%99%80-rest-%EB%AC%B8%EB%B2%95%EC%A0%95%EB%A6%AC-f42efa73d3db" target='_blank'>자바스크립트 Spread문법과 Rest문법</a>
