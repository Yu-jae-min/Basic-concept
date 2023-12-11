# [javascript-algorithm] 프로그래머스 - 2016년

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12901" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12901</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let a = 5;
let b = 24;

function solution1(a, b) {
  const date = new Date(2016, a - 1, b);

  return date.toString().slice(0, 3).toUpperCase();
}

console.log(solution1(a, b)); // "TUE"
```

### - 문제해설

> 1.  Date()생성자를 활용하여 날짜를 가져온다. 이 때 월은 0~11 이기 때문에 -1을 해준다.<br>
> 2.  toStirng()메서드를 활용하여 날짜의 문자열을 정해준다. (Tue May 24 2016 00:00:00 GMT+0900 (한국 표준시))<br>
> 3.  요일을 추출해내기 위해 slice()메서드를 활용하여 0번째부터 3번째전까지의 문자를 추출한다.<br>
> 4.  toUpperCase()메서드를 활용하여 대문자로 변환한다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let a = 5;
let b = 24;

function solution2(a, b) {
  const arr = ["SUN", "MON", "TUE", "WED", "THU", "FRI", "SAT"];
  const date = new Date(`2016-${a}-${b}`);
  const day = date.getDay();

  return arr[day];
}

console.log(solution2(a, b)); // "TUE"
```

### - 문제해설

> 1.  arr변수를 생성하여 일요일~토요일까지의 요일을 배열로 담아둔다. 단, 순서는 getDay의 순서와 일치하도록 일요일부터 넣어둔다.<br>
> 2.  date변수에 Date()생성자를 활용하여 날짜를 가져온다. 이 때 "0000-0-0"의 형태와 같이 작성하는데 벡틱을 이용하여 문자열과 변수를 조합한다.<br>
> 3.  day변수에 요일을 0~6까지 숫자로 반환하는 getDay()메서드를 활용하여 날짜의 index를 가져온다.<br>
> 4.  전체 요일을 배열로 할당한 arr에 지정 날짜의 요일 index를 할당한 변수 day를 index로 하여 출력한다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
let a = 5;
let b = 24;

function solution3(a, b) {
  var dayList = ["FRI", "SAT", "SUN", "MON", "TUE", "WED", "THU"];
  var monthArr = [31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31];
  var daySum;

  if (a < 2) {
    daySum = b - 1;
  } else {
    daySum = monthArr.slice(0, a - 1).reduce((a, b) => a + b) + b - 1;
  }

  return dayList[daySum % 7];
}

console.log(solution3(a, b)); // "TUE"
```

### - 문제해설

> 1.  dayList에 요일을 변수로 담는다. 단 2016년 1월 1일은 금요일이기 때문에 금요일부터 시작하여 담아준다.<br>
> 2.  monthArr에 각 월의 마지막 날짜를 담는다. 다르게 생각하면 요일의 갯수를 담는 것이다.<br>
> 3.  날짜의 합을 더할 빈 변수 daySum을 생성한다.<br>
> 4.  if문을 통해 조건식을 만든다. 최종 연산 방식은 "a월보다 전에 위치하는 모든 월의 날짜 + b의 날짜" 방식으로 계산한다. 1월인 경우 monthArr에서 추출해내어 더하는 값이 없으므로 따로 조건을 만들어 빼준다. 요일에 index가 0부터 시작하므로 -1을 해준다.<br>
> 5.  1월이 아닌 경우 slice()메서드로 a에 해당하는 월 전까지의 모든 월들의 일자를 추출한다. 에를 들어 a가 5인 경우 5-1이 되므로 index 0,4까지 slice되어 1~4월까지의 날짜를 추출하는 것이다. ([31, 29, 31, 30])<br>
> 6.  reduce()메서드를 통해 각각의 요소들을 하나의 값으로 더해준다. (121)<br>
> 7.  하나의 값으로 합쳐진 날에 b만큼의 날을 더해준다. 그 후 요일에 index가 0부터 시작하기 떄문에 -1을 해준다. (144)<br>
> 8.  요일을 할당한 dayList변수에 index를 daySum % 7로 지정하여 나머지 값만큼의 index를 추출한 후 요일을 반환한다.

<br>

## (3) 참고자료

1. <a href="https://dororongju.tistory.com/116" target='_blank'>Date() 생성자</a><br>
2. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date/getDay" target='_blank'>Date.prototype.getDay()</a><br>
3. <a href="https://velog.io/@y_jem/%EA%B8%B0%EB%B3%B8%EA%B0%9C%EB%85%90-%EC%9D%B8%ED%84%B0%ED%94%84%EB%A6%AC%ED%84%B0%EC%99%80-%EC%BB%B4%ED%8C%8C%EC%9D%BC%EB%9F%AC" target='_blank'>인터프리터와 컴파일러</a>
