# [javascript-algorithm] 프로그래머스 - 핸드폰 번호 가리기

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12948" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12948</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let phone_number1 = "01012345678";
let phone_number2 = "0212345678";

function solution(phone_number) {
  let phoneString = String(phone_number);
  let answer = "*".repeat(phoneString.length - 4) + phoneString.slice(-4);

  return answer;
}

console.log(solution(phone_number1)); // *******5678
console.log(solution(phone_number2)); // ******5678
```

### - 문제해설

> 1.  함수안에 새로운 변수 phoneString를 만들어 문자열로 바꾸어 넣어준다.<br>
> 2.  repeat() 함수를 활용하여 \* 를 반복시킨다. 반복시킬 횟수는 전달받은 문자열의 길이 -4 로 지정한다. 이유는 노출될 번호가 전달받은 문자열 뒷자리 네자리 수 이기 때문이다.<br>
> 3.  slice() 메소드를 이용하여 뒷자리 네자리 수를 가져온다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let phone_number1 = "01012345678";
let phone_number2 = "0212345678";

function solution(phone_number) {
  var result = "";

  for (let i = 0; i < phone_number.length; i++) {
    result += i < phone_number.length - 4 ? "*" : phone_number.charAt(i);
  }
  return result;
}

console.log(solution(phone_number1)); // *******5678
console.log(solution(phone_number2)); // ******5678
```

### - 문제해설

> 1.  for문을 이용하여 매개변수의 길이만큼 반복한다.<br>
> 2.  result 변수에 순차적으로 필요한 값을 할당한다. 삼항연산자를 활용하는데 i값이 매개변수길이-4 보다 적을 경우 \* 을 할당하고 i값이 매개변수길이-4보다 같거나 커질경우 매개변수의 특정 인덱스의 단일문자를 추가하여준다.

<br>

## (3) 참고자료

1. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/repeat" target='_blank'>String.prototype.repeat()</a><br>
2. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/slice" target='_blank'>String.prototype.slice()</a><br>
3. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/charAt" target='_blank'>String.prototype.charAt()</a>
