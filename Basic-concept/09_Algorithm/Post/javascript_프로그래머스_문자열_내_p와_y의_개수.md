# [javascript-algorithm] 프로그래머스 - 문자열 내 p와 y의 개수

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12916" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12916</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let s = "pPoooyY";

function solution1(s) {
  let lower = s.toLowerCase();
  let spl = lower.split("");
  let pCount = 0;
  let yCount = 0;

  for (let i = 0; i < s.length; i++) {
    if (spl[i] == "p") {
      pCount += 1;
    } else if (spl[i] == "y") {
      yCount += 1;
    }
  }
  return pCount + yCount === 0 ? true : pCount === yCount ? true : false;
}

console.log(solution1(s)); // true
```

### - 문제해설

> 1.  대소문자의 구분이 없기 때문에 새로운 변수 lower를 생성하여 대문자나 소문자 중 하나를 선택하여 문자를 변환하여 할당한다.<br>
> 2.  반복문에서 사용하기 위해 문자를 split()메서드를 이용하여 개별로 나누어 배열에 담는다.<br>
> 3.  p와 y의 갯수를 카운팅 할 변수를 생성한다.<br>
> 4.  반복문을 사용하는데 전체 배열 요소의 length만큼 반복한다. 중첩으로 조건문을 활용하여 배열 요소 index의 문자가 "p" 혹은 "y" 일 경우 생성해놓은 변수에 1씩 누적하여 더해준다.<br>
> 5.  출력값은 삼항연산자를 중첩으로 사용하여 p와 y의 카운팅이 0 일때 true를 출력하고, 아닌 경우 p의 갯수와 y의 갯수가 같으면 true, 다르면 false를 출력한다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let s = "pPoooyY";

function solution2(s) {
  return (
    s.toUpperCase().split("P").length === s.toUpperCase().split("Y").length
  );
}

console.log(solution2(s)); // true
```

### - 문제해설

> 1.  대소문자의 구분이 없기 때문에 toUpperCase()메서드로 대문자로 통일 시킨다.<br>
> 2.  split()메서드를 활용하여 문자열을 자르는데 기준을 "P" 혹은 "Y"를 잘라낸다.<br>
> 3.  잘라낸 문자열의 length를 추출하여 비교한다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
let s = "pPoooyY";

function solution3(s) {
  return s.match(/p/gi).length == s.match(/y/gi).length;
}

console.log(solution3(s)); // true
```

### - 문제해설

> 1.  match()메서드를 이용하여 p혹은 y를 검색한다. 파라미터값으로 들어간 정규식과 문자열을 매칭하여 찾아주는데 대소문자 구분없이 검색되도록 i플래그를 사용하고 g플래그로 문자 전체를 검색한다.<br>
> 2.  length속성으로 match()메서드로 찾아낸 문자의 갯수를 찾아낸다.<br>
> 3.  비교연산자를 사용하여 p와 y의 갯수를 비교한다. 같으면 true, 다르면 false를 반환한다.

<br>

## (3) 참고자료

1. <a href="https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=diceworld&logNo=220173778957" target='_blank'>toUpperCase / toLowerCase</a><br>
2. <a href="https://webisfree.com/2014-11-28/[%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8]-%EB%8F%99%EC%9D%BC%ED%95%9C-%EB%8B%A8%EC%96%B4%EB%A5%BC-%EB%AC%B8%EC%9E%90%EC%97%B4%EC%97%90%EC%84%9C-%EC%B0%BE%EA%B8%B0-match()-%ED%95%A8%EC%88%98" target='_blank'>String.prototype.match()</a><br>
3. <a href="https://ko.javascript.info/regexp-introduction" target='_blank'>정규식 플래그</a><br>
4. <a href="http://tcpschool.com/javascript/js_operator_comparison" target='_blank'>비교연산자</a>
