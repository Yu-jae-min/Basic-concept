# [javascript-algorithm] 프로그래머스 - 체육복

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/42862" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/42862</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
const n = 5;
const lost = [2, 4];
const reserve = [1, 3, 5];

function solution1(n, lost, reserve) {
  return (
    n -
    lost.filter((a) => {
      const b = reserve.find((r) => Math.abs(r - a) <= 1);
      if (!b) return true;
      reserve = reserve.filter((r) => r !== b);
    }).length
  );
}

console.log(solution1(n, lost, reserve));
```

### - 문제해설

> 1.  체육복을 잃어버린 lost배열에 filter메서드를 활용한다. (잃어버린 사람 중에 빌린 사람들을 제거)<br>
> 2.  b변수에 여유번호 - 잃은번호가 1차이 나는지 확인하여 조건을 만족하는 첫번째 요소를 담는데 이 때 절대값으로 확인하기 위해 Math.abs()함수를 활용한다.<br>
> 3.  if문으로 undefined를 체크한다. 만약 체육복을 빌릴 사람이 없는 경우 b값은 undefined가 되고 undefined인 경우 !(NOT연산)에 의해 true를 출력하여 lost배열안에서 제거되지 않는다. 또한 빌릴 사람이 있는 경우 undefined가 아니므로 해당 조건문에 true가 출력되지 않아 true가 없으므로 조건을 만족하지 못한다고 판단하여 lost배열에서 삭제된다.<br>
> 4.  최종 출력값이 true가 아닌 경우(lost의 배열 요소가 체육복을 빌렸을 경우) 빌려준 사람은 이제 체육복을 빌려주지 못하기 때문에 배열에서 제거하기 위해 reserve변수에 reserve.filter메서드를 활용하여 제거한다.
>     (여벌을 챙겼으나 도난당한 학생에 대한 처리가 안되었음)

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
const n = 5;
const lost = [2, 4];
const reserve = [1, 3, 5];

function solution2(n, lost, reserve) {
  const students = {};
  let answer = 0;
  for (let i = 1; i <= n; i++) {
    students[i] = 1;
  }
  lost.forEach((number) => (students[number] -= 1));
  reserve.forEach((number) => (students[number] += 1));

  for (let i = 1; i <= n; i++) {
    if (students[i] === 2 && students[i - 1] === 0) {
      students[i - 1]++;
      students[i]--;
    } else if (students[i] === 2 && students[i + 1] === 0) {
      students[i + 1]++;
      students[i]--;
    }
  }

  for (let key in students) {
    if (students[key] >= 1) {
      answer++;
    }
  }

  return answer;
}

console.log(solution2(n, lost, reserve));
```

### - 문제해설

> 1.  빈 객체 students를 생성하고 for문을 활용하여 객체에 value값을 할당한다. ({1: 1, 2: 1, 3: 1, 4: 1, 5: 1})<br>
> 2.  forEach문을 활용하여 읽어버린 애들은 -1, 여유분을 갖고 온 아이들은 +1 한다. ({1: 2, 2: 0, 3: 2, 4: 0, 5: 2})<br>
> 3.  두번째 for문을 통해 자기 자신의 체육복이 2개이고 뒷 번호 혹은 앞 번호가 체육복이 없을 때 증감연산자를 활용하여 자기 자신의 체육복을 -1, 빌려준 학생의 체육복을 +1 한다. ({1: 1, 2: 1, 3: 1, 4: 1, 5: 2})<br>
> 4.  세번째 for in문을 통해 students객체를 순환하며 value값(체육복 갯수)가 1보다 크거나 같은 경우 answer을 증감하여 수업을 들을 수 있는 학생의 수를 출력한다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
const n = 5;
const lost = [2, 4];
const reserve = [1, 3, 5];

let tmp = reserve.slice();

function solution3(n, lost, reserve) {
  let tmp = reserve.slice();

  for (let i in tmp) {
    let key = lost.indexOf(tmp[i]);

    if (key != -1) {
      lost.splice(key, 1);
      reserve.splice(reserve.indexOf(tmp[i]), 1);
    }
  }

  for (let i of reserve) {
    let key = lost.includes(i - 1) ? lost.indexOf(i - 1) : lost.indexOf(i + 1);

    if (key != -1) {
      lost.splice(key, 1);
    }
  }

  return n - lost.length;
}

console.log(solution3(n, lost, reserve));
```

### - 문제해설

> 1.  첫번째 for문은 여벌 체육복을 가지고 있는데 도난을 당한 경우를 확인한다. for in문을 통해 배열 index를 순환하고 if문을 통해 reserve요소가 lost에 포함되어있는 경우 즉 여벌 체육복을 가지고 있느데 도난을 당한 경우 lost와 reserve에서 splice()메서드를 활용하여 자기 자신 요소를 삭제한다.<br>
> 2.  두번째 for문은 여벌 체육복을 가지고 온 학생에게 체육복을 빌린 경우를 확인한다. for of문을 통해 reserve배열 요소를 순환하고 배열 요소의 앞 번호 뒷 번호가 lost에 포함되어 있을 경우 해당 번호를 lost에서 삭제한다.<br>
> 3.  출력 값은 모든 학생의 수 n에서 도난 당한 사람 중 빌린 사람을 삭제한 배열 요소 lost에 length를 빼준다.

<br>

## (3) 참고자료

1. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/filter" target='_blank'>Array.prototype.filter()</a><br>
2. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/find" target='_blank'>Array.prototype.find()</a><br>
3. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/abs" target='_blank'>Math.abs()</a><br>
4. <a href="https://velog.io/@eomttt/for-...in-for-...of-%EC%B0%A8%EC%9D%B4" target='_blank'>for in, for of</a><br>
5. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/splice" target='_blank'>Array.prototype.splice()</a><br>
6. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/includes" target='_blank'>Array.prototype.includes()</a>
