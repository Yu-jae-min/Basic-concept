# [javascript-algorithm] 프로그래머스 - 비밀지도

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/17681" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/17681</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
const n = 5;
const arr1 = [9, 20, 28, 18, 11];
const arr2 = [30, 1, 21, 17, 28];

function solution1(n, arr1, arr2) {
  return arr1.map((v, i) =>
    addZero(n, (v | arr2[i]).toString(2)).replace(/1|0/g, (a) =>
      +a ? "#" : " "
    )
  );
}

const addZero = (n, s) => {
  return "0".repeat(n - s.length) + s;
};

console.log(solution1(n, arr1, arr2));
```

### - 문제해설

> 1. map()메서드를 활용하여 arr1 배열 요소에 접근한다.<br>
> 2. addZero 변수에 자릿수를 채워줄 함수를 할당한다. 2진수 변환 시 생략되는 '0'을 추가해주는데 문자의 길이는 n - s.length로 설정하여 길이가 n보다 짧은 문자열에만 추가한다. 이 때 매개변수 s는 (v | arr2[i]).toString(2)가 되는데 여기서 비트연산자 |를 통해 두 개의 2진수 각 자릿수를 더해주는 역할을 하게 된다. |은 2진수 값을 비교하여 둘 중 하나의 비트가 1이라면 1을 반환한다. 또 toString(2)를 통해 각 배열 요소를 2진수로 변환한다. 그리고 2진수는 반환 된 값에 선두에 오는 숫자가 0일 경우 생략되는데 이를 repeat()메서드를 통해 '0'으로 채우게 된다.<br>
> 3. addZero를 map()메서드의 콜백함수로 사용한다. addZero를 통해 2진수로 변환한 값을 replace()메서드를 통해 #과 공백으로 치환한다. 이 때 치환되는 문자는 모든 전체 문자열 중 1혹은 0일 경우에 치환되며 치환되는 값은 화살표 함수에 삼항연산자를 활용한다. 이 때 +기호를 추가하여 Number타입으로 형 변환 후 비교한다. 0을 초과하는 경우 true이므로 #으로 치환되고 0일 경우 false가 되어 공백을 치환된다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
const n = 5;
const arr1 = [9, 20, 28, 18, 11];
const arr2 = [30, 1, 21, 17, 28];

function solution2(n, arr1, arr2) {
  let num1, num2, s;
  let answer = [];

  for (let i = 0; i < n; i++) {
    num1 = arr1[i];
    num2 = arr2[i];
    s = "";
    for (let j = 0; j < n; j++) {
      s = (num1 % 2) + (num2 % 2) ? "#" + s : " " + s;
      num1 = Math.floor(num1 / 2);
      num2 = Math.floor(num2 / 2);
    }
    answer.push(s);
  }
  return answer;
}

console.log(solution2(n, arr1, arr2));
```

### - 문제해설

> 1.  변수 num1, num2, s;를 선언하고 빈 배열 answer를 생성한다.<br>
> 2.  for문을 이용하여 각각의 배열 요소를 비교한다. 이 때 num1과 num2에 인자로 받은 i번째 배열 요소를 할당한다.<br>
> 3.  for문안에 for문을 이용하여 배열요소의 각 자릿수를 순회하고 2진수값을 구한다. 2진수 값을 구한 뒤 더하고 삼항연산자를 이용하여 더한 값이 0보다 클 경우 #, 아닌 경우 공백을 s에 더하여준다. 또한 배열요소의 각 자릿수 순회가 끝나면 빈 배열 answer에 push()메서드를 활용하여 #과 공백이 할당된 문자를 배열로 추가한다. (2진수 계산법 : 예를 들어 20의 2진수는 20%2 = 0, 10%2 = 0, 5%2 = 1, 2%2 = 0, 1%2 = 1이 되므로 역순으로 읽어 10100이 된다.)

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
const n = 5;
const arr1 = [9, 20, 28, 18, 11];
const arr2 = [30, 1, 21, 17, 28];

const solution3 = (n, arr1, arr2) => {
    const binaryStringArray1 = decimalToBinary(arr1, n);
    const binaryStringArray2 = decimalToBinary(arr2, n);
    const map1 = binaryStringArray1.map(splitToNumbers)
    const map2 = binaryStringArray2.map(splitToNumbers)
    const combinedMap = sumArray(map1, map2);

    return numberToSharpAndEmpty(combinedMap).map(v => v.join(''));
}

const numberToSharpAndEmpty = (arr) => {
    return arr.map((v1, i1) => {
        return v1.map((v2, i2) => {
            return (v2 === 0) ? ' ' : '#';
        }
    )})
};

const sumArray = (arr1, arr2) => arr1.map((v1, i1) => v1.map((v2, i2) => v2 + arr2[i1][i2]));
const decimalToBinary = (array, n) => array.map(item => item.toString(2).padStart(n, '0'));
const splitToNumbers = (str) => str.split('').map(e => Number(e));

console.log(solution3(n, arr1, arr2)) mislav
```

### - 문제해설

> 1.  decimalToBinary 변수에 2진수로 변환하는 함수를 넣는다. map()메서드를 활용하는데 각 배열요소를 toString(2)를 활용하여 2진수로 바꾼 뒤 padStart()메서드로 length가 n보다 작은 경우 문자열 앞에 0을 추가하도록 한다.<br>
> 2.  decimalToBinary 변수를 binaryStringArray1, binaryStringArray2에 각각 할당하고 비교해야하는 배열을 매개변수로 받는다.
>     // ['01001', '10100', '11100', '10010', '01011']<br>
> 3.  splitToNumbers 변수에 2진수로 바꾼 배열요소를 split()메서드를 통해 개별로 나눈 뒤 Number타입으로 형 변환시킨다.<br>
> 4.  splitToNumbers 변수에 담긴 함수를 2진수로 바꾼 배열에 적용시키기 위해 map1변수와 map2 변수에 할당한다.
>     // [[0, 1, 0, 0, 1], [1, 0, 1, 0, 0], [1, 1, 1, 0, 0], [1, 0, 0, 1, 0], [0, 1, 0, 1, 1]]<br>
> 5.  두 개의 배열 요소를 합치기 위해 sumArray변수에 map()메서드를 중첩으로 사용한다. v는 배열 내 현재 값, i는 배열 내 현재 값의 인덱스이 된다. v1은 배열안의 배열이 되고, 배열안의 배열을 또다시 맵핑하여 v2는 배열안의 배열에 요소가 된다. v2 + arr2[i1][i2]를 통해 arr1에 배열안의 배열에 요소 값에 arr2의 배열안에 배열 요소를 더하게 된다.<br>
> 6.  combinedMap 변수에 배열 요소를 더하는 함수가 담긴 sumArray변수를 할당하고 매개변수로 map1, map2를 전달한다.
>     // [[1, 2, 1, 1, 1], [1, 0, 1, 0, 1], [2, 1, 2, 0, 1], [2, 0, 0, 1, 1], [1, 2, 1, 1, 1]]<br>
> 7.  더해진 배열 요소를 지정 문자 #과 공백으로 바꾸어주기 위 numberToSharpAndEmpty변수에 위와 같이 중복 map()메서드를 활용하여 배열안에 배열의 요소에 접근 후 비교연산자를 활용하여 0과 같은 경우 공백을 반환하고, 아닌 경우 #을 반환하는 함수를 할당한다.<br>
> 8.  numberToSharpAndEmpty함수에 매개변수 combinedMap를 전달한 뒤 해당 값을 map()메서드와 join()메서드를 통해 하나의 값으로 합친 뒤 반환한다.

<br>

## (3) 참고자료

1. <a href="https://medium.com/gdana/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EB%B9%84%ED%8A%B8-%EC%97%B0%EC%82%B0%EC%9E%90-5f772ffa35e8" target='_blank'>비트연산자</a><br>
2. <a href="https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=hasll&logNo=70000641526" target='_blank'>2진수 계산법</a><br>
3. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/padStart" target='_blank'>String.prototype.padStart()</a><br>
4. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/replace" target='_blank'>String.prototype.replace()</a>
