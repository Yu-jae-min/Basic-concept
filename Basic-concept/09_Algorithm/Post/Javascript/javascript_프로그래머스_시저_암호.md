# [javascript-algorithm] 프로그래머스 - 시저 암호

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12926" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12926</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let s = "a B z";
let n = 4;

function solution1(s, n) {
  var upper = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
  var lower = "abcdefghijklmnopqrstuvwxyz";
  var answer = "";

  for (var i = 0; i < s.length; i++) {
    var text = s[i];
    if (text == " ") {
      answer += " ";
      continue;
    }
    var textArr = upper.includes(text) ? upper : lower;
    var index = textArr.indexOf(text) + n;
    if (index >= textArr.length) index -= textArr.length;
    answer += textArr[index];
  }
  return answer;
}

console.log(solution1(s, n)); // e F d
```

### - 문제해설

> 1.  대문자, 소문자, 빈 문자열이 할당되어있는 변수를 만든다.<br>
> 2.  반복문을 이용하여 문자열을 차례대로 비교한다.<br>
> 3.  문자가 공백인 경우 공백을 반환해야하므로 조건문을 이용하여 공백일 경우 공백을 반환하며 continue를 통해 공백인 경우 아래 코드를 무시하고 다음 반복문을 실행한다.<br>
> 4.  textArr변수에 includes()메서드로 boolean값을 추출한 뒤 대문자일 경우 좌항, 소문자일 경우 우항을 할당한다.<br>
> 5.  전체 문자열 textArr변수안에 indexOf()메서드로 문자의 index를 찾아내고 그 index에 n을 더한 값을 index변수에 할당한다.<br>
> 6.  index의 값이 전체 문자열의 길이보다 큰 경우 (s의 문자가 Z,z일 경우) 조건문을 만든다. index값에 textArr.length를 빼주어 재할당한다.<br>
> 7.  answer변수에 textArr[index]를 할당한 뒤 출력한다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let s = "a B z";
let n = 4;

function solution2(s, n) {
  return s
    .split("")
    .map((value) => {
      if (value === " ") return value;
      return value.toUpperCase().charCodeAt() + n > 90
        ? String.fromCharCode(value.charCodeAt() + n - 26)
        : String.fromCharCode(value.charCodeAt() + n);
    })
    .join("");
}

console.log(solution2(s, n)); // e F d
```

### - 문제해설

> 1.  split()메서드로 문자를 개별로 분리한 뒤 배열에 담는다.<br>
> 2.  개별로 분리한 각각의 배열 요소에 함수를 적용시키기 위해 map()메서드를 활용한다.<br>
> 3.  조건문을 통해 문자가 공백일 경우는 문자 그대로 출력한다.<br>
> 4.  미국 표준 정보교환 코드인 아스키코드(10진수)를 활용하는데 첫번째로 value를 toUpperCase()메서드를 통해 대문자로 변환시킨 뒤 charCodeAt()메서드로 문자열을 아스키코드 값으로 바꾼다. 아스키코드로 바꾼 값을 n값과 더한 뒤 그 결과값이 90이상일 경우 true, 90미만일 경우 false를 출력한다. 이유는 아스키코드 90을 넘어가는 값을 찾아내기 위해서인데 90을 넘어가는 값은 Z를 넘어가는 값이기 때문이다.<br>
> 5.  결과값이 true인 경우 value의 아스키코드 + n에 26을 빼주어 A부터 시작한 값을 출력한다. 또한 아스키코드를 문자열로 변환시키기 위해 String.fromCharCode() 매서드를 활용한다.<br>
> 6.  결과값이 false인 경우 value의 아스키코드 + n 값을 출력한다. 또한 아스키코드를 문자열로 변환시키기 위해 String.fromCharCode() 매서드를 활용한다.<br>
> 7.  배열의 담긴 각각의 요소를 join()메서드를 통해 하나의 값으로 만든다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
let s = "a B z";
let n = 4;

function solution3(s, n) {
  var chars =
    "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyABCDEFGHIJKLMNOPQRSTUVWXYZABCDEFGHIJKLMNOPQRSTUVWXY                          ";
  return s
    .split("")
    .map((e) => chars[chars.indexOf(e) + n])
    .join("");
}

console.log(solution3(s, n)); // e F d
```

### - 문제해설

> 1.  문제의 조건 중 n은 25 이하인 것을 활용하여 문자가 z인 경우 최대 25까지 밀리는 것을 감안하여 문자를 중복하여 작성한 후 chars변수에 할당한다.<br>
> 2.  split()메서드로 문자를 개별로 분리한 뒤 배열에 담는다.<br>
> 3.  개별로 분리한 각각의 배열 요소에 함수를 적용시키기 위해 map()메서드를 활용한다.<br>
> 4.  전체 문자열에서 해당 요소 e의 index를 indexOf()메서드로 추출한 뒤 n과 더한 값을 chars의 index값으로 하여 추출한다.<br>
> 5.  배열의 담긴 각각의 요소를 join()메서드를 통해 하나의 값으로 만든다.

<br>

## (2) 문제풀이 및 해설 4

### - 문제풀이

```javascript
let s = "a B z";
let n = 4;

function solution4(s, n) {
  var result = s.replace(
    /[a-z]/gi,
    (c) =>
      [
        (c = c.charCodeAt(0)),
        String.fromCharCode((c & 96) + (((c % 32) + n - 1) % 26) + 1),
      ][1]
  );

  return result;
}

console.log(solution4(s, n)); // e F d
```

### - 문제해설

> 1.  replace()메서드를 활용하여 각각의 문자를 새로운 문자로 반환한다.<br>
> 2.  replace 첫번째 속성은 변환되는 대상이다. 정규표현식을 활용한다. /[a-z]/로 전체 문자열을 설정하고 i,g플래그로 옵션을 설정한다. (i는 대소문자를 구별하지 않고 검색, g는 모든 패턴을 검색)<br>
> 3.  replace 두번째 속성은 변환되는 값이다. 우선 c = c.charCodeAt(0)를 통해 자신의 유니코드 값을 할당한다.<br>
> 4.  첫번째로 c & 96 를 통해 대소문자를 구분한다. 2진법으로 대문자의 코드들은 1000001~1011010, 소문자는 1100001~1111010라서 앞에 2자리로 빼고는 같다. 10진수 96의 2진수는 1100000인데 비트연산자를 통해 자신의 유니코드 값과 1100000 을 비트연산하여 앞의 2자리를 추출하여 대소문자를 구분한다. 여기서 96을 사용한 이유는 뒤의 5자리가 0이기 때문에 사용한 것이다. 비트연산 중 하나의 값이라도 0일 경우 0을 반환하기 때문이다. 그러므로 96을 사용하면 뒤에 5자리는 모두 0으로 처리된다.<br>
> 5.  두번째로 뒤에 나머지 5자리를 가져오기 위해 c % 32 를 실행한다. 예를 들어 b인 경우 2진수가 1100010 이므로 1100010 % 100000 = 10 이 연산되고, 숫자로 2가 된다. 왜냐하면 숫자2는 10진법으로 110010가 되기 때문이다. 여기에 n값이 더해지고 a가 1부터 시작하기 때문에 나머지 계산을 위해 '- 1'을 해서 초기점을 0으로(00000~11001) 잡아준다. 그럼 0~25의 숫자 중 하나가 나오고 여기서 n만큼 더해준 뒤 26으로 나머지 계산을 하고 다시 아까 빼 준 1을 다시 더한다.

<br>

## (3) 참고자료

1. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/continue" target='_blank'>continue</a><br>
2. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf" target='_blank'>indexOf</a><br>
3. <a href="https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=diceworld&logNo=220175224345" target='_blank'>charCodeAt / fromCharCode</a><br>
4. <a href="https://www.ibm.com/docs/ko/aix/7.1?topic=adapters-ascii-decimal-hexadecimal-octal-binary-conversion-table" target='_blank'>아스키코드 변환표</a><br>
5. <a href="https://poiemaweb.com/js-regexp">정규표현식</a><br>
6. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Bitwise_AND" target='_blank'>비트연산자</a>
