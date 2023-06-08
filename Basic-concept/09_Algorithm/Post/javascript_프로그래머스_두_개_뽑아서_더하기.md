# [javascript-algorithm] 프로그래머스 - 두 개 뽑아서 더하기

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/68644?language=javascript" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/68644?language=javascript</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let numbers = [5, 0, 2, 7];

function solution1(numbers) {
  let answer = [];

  for (let i = 0; i < numbers.length - 1; i++) {
    for (let j = i + 1; j < numbers.length; j++) {
      answer.push(numbers[i] + numbers[j]);
    }
  }

  let result = [...new Set(answer)];

  return result.sort((a, b) => a - b);
}

console.log(solution1(numbers));
```

### - 문제해설

> 1.  for문을 중복으로 사용한다. for문 내부 for문의 변수 j는 더해지는 index값이 되므로 i+1로 할당하여 기준이 되는 값에 index와 중복해서 더해지는 것을 피한다.<br>
> 2.  더한 값을 push()메서드로 빈 배열에 추가해준다.<br>
> 3.  첫번째 for문에 반복 조건은 numbers.length에 -1을 해준다. 마지막 index 값은 이미 연산이 진행되어 연산이 진행되지 않아도 되기 때문이다.<br>
> 4.  배열의 중복되는 값을 제거하기 위해 Set 객체를 활용한다. 이 때 배열로 생성해야하기 때문에 대괄호안에 Set 객체를 생성하고 이 때 객체로 들어가지 않고 배열로 들어가야하므로 요소를 펼쳐주는 스프레드 연산자를 활용한다.<br>
> 5.  출력하기 전 출력 값을 sort()메서드를 활용하여 오름차순으로 정렬해준다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let numbers = [5, 0, 2, 7];

function solution2(numbers) {
  var answer = [];

  for (var i = 0; i < numbers.length - 1; i++) {
    for (var j = i + 1; j < numbers.length; j++) {
      if (!answer.includes(numbers[i] + numbers[j])) {
        answer.push(numbers[i] + numbers[j]);
      }
    }
  }

  return answer.sort((a, b) => a - b);
}

console.log(solution2(numbers));
```

### - 문제해설

> 전체적인 풀이는 위의 문제와 같으며 if문을 추가하였다. if문 조건으로 불린 타입을 반환하는 includes()메서드를 활용하여 해당 사이클에서 연산되는 값이 존재하지 않을 경우 push하도록 하여 중복을 제거하였다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
let numbers = [5, 0, 2, 7];

function solution3(numbers) {
  var answer = [];

  numbers.forEach((v) => {
    // 5
    const num1 = numbers.slice();

    let a = numbers.indexOf(v);
    num1.splice(a, 1); // 0 2 7

    num1.forEach((z) => {
      let num2 = v + z;

      if (!answer.includes(num2)) {
        answer.push(num2);
      }
    });
  });

  return answer.sort((a, b) => a - b);
}

console.log(solution3(numbers));
```

### - 문제해설

> 1.  forEach()메서드로 배열 각 요소에 함수를 실행한다. (첫번째 사이클에서 5)<br>
> 2.  num1 변수에 numbers 요소를 slice()메서드를 활용하여 기존 배열을 얇게 복사하여 저장한다. (전체배열 5, 0, 2, 7)<br>
> 3.  a변수에 indexOf()메서드를 활용하여 함수가 실행되고 있는 자신의 index를 추출한다. (첫번째 사이클 5의 index 0)<br>
> 4.  num1 변수를 splice()메서드를 활용하여 잘라내는데 a변수를 기준으로 잘라내어 기존 배열 - 함수가 실행되는 배열요소의 형태에 배열로 수정한다. (전체 배열 중 index 0부터 1개의 요소를 삭제, 즉 5가 삭제 되어 0, 2, 7이 됨)<br>
> 5.  forEach()메서드를 중첩하여 실행한다. 이 때 기준이 되는 요소는 num1의 각 요소가 된다.<br>
> 6.  실행문에서는 num2변수에 첫번째 forEach을 실행한 요소(v, 5) + 실행한 요소를 잘라낸 나머지 요소(z, 0 2 7)를 더하여 할당한다.<br>
> 7.  push()메서드로 answer변수에 num2를 넣는데 includes()메서드를 활용하여 num2와 같은 값이 존재하지 않을 경우만 push한다.<br>
> 8.  출력하기 전 출력 값을 sort()메서드를 활용하여 오름차순으로 정렬해준다.

<br>

## (3) 참고자료

1. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Set" target='_blank'>Set객체</a><br>
2. <a href="https://paperblock.tistory.com/62" target='_blank'>Spread Operator(스프레드 연산자)</a><br>
3. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/includes" target='_blank'>Array.prototype.includes()</a><br>
4. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach" target='_blank'>Array.prototype.forEach()</a>
