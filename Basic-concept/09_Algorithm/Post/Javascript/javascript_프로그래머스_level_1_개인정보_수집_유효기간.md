# [Algorithm] 프로그래머스 Level 1 - 개인정보 수집 유효기간

2023년 09월 05일

<br>

## 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/150370

<br>
<br>

## 2. 나의 풀이

```jsx
const mySolution = (today, terms, privacies) => {
  var answer = [];

  const todayDate = new Date(today);
  const termsDate = {};

  terms.forEach((item) => {
    const [termsName, termsDay] = item.split(" ");

    termsDate[termsName] = Number(termsDay);
  });

  privacies.forEach((item, index) => {
    const [dateItem, termsItem] = item.split(" ");

    const expiryDate = new Date(dateItem);
    expiryDate.setMonth(expiryDate.getMonth() + termsDate[termsItem]);
    expiryDate.setDate(expiryDate.getDate() + -1);

    if (expiryDate < todayDate) answer.push(index + 1);
  });

  return answer;
};

console.log(
  mySolution(
    "2022.05.19",
    ["A 6", "B 12", "C 3"],
    ["2021.05.02 A", "2021.07.01 B", "2022.02.19 C", "2022.02.20 C"]
  )
); // [1, 3]
```

1. 현재 날짜를 Date 타입으로 바꿔 `todayDate` 변수에 할당하였다.
2. 파라미터로 전달받은 terms 배열 요소를 객체 프로퍼티로 활용하기 위해 변수 `termsDate`를 생성하고 `forEach`문으로 순회하며 문자열을 요소의 약관 타입과 약관 개월 수로 나누어 객체 key, value로 저장하였다.
3. 고객의 약관 타입과 유효 날짜가 담긴 파라미터 `privacies`를 `forEach`로 순회하는데 내부에서는 `split` 메소드를 통해 약관 타입과 날짜를 나눈 뒤 약관 날짜를 Date 타입으로 바꾸고 약관 타입에 맞는 개월 수를 더해주었다. 그 후 날짜에 1일을 빼주었다. 문제 조건 중 한달은 28일이라는 가정이 있었는데 약관 타입의 경우 어차피 월 단위로 주어지기 때문에 월에 더해준 것이다. 그 후 날짜에 하루를 빼주어 유효 기간 날짜를 맞추었다.
4. `if` 조건문을 활용하여 유효기간이 지났는지 확인 후 유효기간이 지났다면 현재 index에 1을 더한 후 `answer`에 `push` 하여 출력하였다.

<br>
<br>

## 3. 인기 풀이

```jsx
const othersSolution = (today, terms, privacies) => {
  var answer = [];
  var [year, month, date] = today.split(".").map(Number);
  var todates = year * 12 * 28 + month * 28 + date;
  var t = {};

  terms.forEach((e) => {
    let [a, b] = e.split(" ");
    t[a] = Number(b);
  });

  privacies.forEach((e, i) => {
    var [day, term] = e.split(" ");
    day = day.split(".").map(Number);

    var dates = day[0] * 12 * 28 + day[1] * 28 + day[2] + t[term] * 28;

    if (dates <= todates) answer.push(i + 1);
  });

  return answer;
};

console.log(
  othersSolution(
    "2022.05.19",
    ["A 6", "B 12", "C 3"],
    ["2021.05.02 A", "2021.07.01 B", "2022.02.19 C", "2022.02.20 C"]
  )
); // [1, 3]
```

1. 현재 날짜를 `split` 메소드로 자른 후 `map` 메소드로 순회하며 Number 타입으로 바꾸고 구조 분해 할당하여 `year`, `month`, `date` 변수에 할당하였다.
2. 현재 날짜 `year`, `month`, `date` 변수를 숫자로 변환하여 할당하는데 한 달은 28일로 취급하므로 28일로 고정하고 연도, 월, 일을 숫자로 바꾸어 합산하여 `todates` 변수에 할당하였다.
3. 파라미터로 전달받은 terms 배열 요소를 객체 프로퍼티로 활용하기 위해 변수 `t`를 생성하고 `forEach`문으로 순회하며 문자열을 요소의 약관 타입과 약관 개월 수로 나누어 객체 key, value로 저장하였다.
4. 고객의 약관 타입과 유효 날짜가 담긴 파라미터 `privacies`를 `forEach`로 순회하는데 내부에서는 `split` 메소드를 통해 약관 타입과 날짜를 나눈 뒤 날짜가 담긴 `day` 변수에 날짜를 `split` 메소드로 자른 후 `map` 메소드로 순회하며 Number 타입으로 바꾸어 재할당하였다. 그 후 만료 날짜가 담긴 day를 숫자로 변환하였다.
5. `if` 조건문을 활용하여 만료 날짜가 현재 날짜보다 작거나 같은 지 확인 후 맞다면 현재 index에 1을 더하여 `answer`에 `push` 한 후 출력하였다.

<br>
<br>

## 4. 비교

나의 풀이와 인기 풀이의 속도, 가독성은 크게 차이가 없었던 것 같다. 하지만 나의 풀이의 경우 Date 타입을 고집해가며 풀었고 인기 풀이의 경우 날짜는 생각하지 않고 한 달은 28일로 가정한다는 조건을 정확히 적용하여 숫자 값으로 변환한 뒤 비교하였다. 나의 풀이의 경우도 모든 테스트 케이스를 통과하기는 했지만 테스트 케이스를 통과하기 위해 꾸역꾸역 작성한 느낌이 없지않아 있는 것 같다. Date 타입이 들어가는 경우 실제 날짜와 싱크가 어긋나면 안된다는 강박 관념이 있었던 것 같다. 하지만 이 문제의 경우 한 달이 28일로 가정한다는 조건이 붙어있었기에 Date 타입을 고집하며 푸는 것보다는 인기 풀이와 같이 정확한 연산을 통한 비교로 정확하게 푸는 것이 더 좋은 풀이라고 생각된다.

<br>
