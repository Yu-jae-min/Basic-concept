# [javascript-algorithm] 프로그래머스 - 모의고사

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/42840?language=javascript" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/42840?language=javascript</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
const answers = [1, 3, 2, 4, 2];

function solution1(answers) {
  const answer = [];
  const mathGiver = [
    [1, 2, 3, 4, 5],
    [2, 1, 2, 3, 2, 4, 2, 5],
    [3, 3, 1, 1, 2, 2, 4, 4, 5, 5],
  ];
  const count = [0, 0, 0];

  for (let i = 0; i < answers.length; i++) {
    if (mathGiver[0][i % mathGiver[0].length] == answers[i]) count[0]++;
    if (mathGiver[1][i % mathGiver[1].length] == answers[i]) count[1]++;
    if (mathGiver[2][i % mathGiver[2].length] == answers[i]) count[2]++;
  }

  for (let j = 0; j < count.length; j++) {
    if (count[j] == Math.max(...count)) answer.push(j + 1);
  }

  return answer;
}

console.log(solution1(answers));
```

### - 문제해설

> 1.  각 수포자의 찍는 패턴을 mathGiver 변수에 배열로 담아둔다.<br>
> 2.  for문을 활용하여 각 수포자의 패턴이 정답일 경우 answerCount변수에 해당 index 요소를 증감시키는데 이 때 if문을 활용하여 조건을 넣는다. 조건은 수포자의 패턴인 mathGiver배열의 요소를 정답이 담긴 answers의 배열과 비교하는 것인데 이 때 배열안의 배열 요소 접근 시 i값을 mathGiver배열의 요소 length로 나눈 나머지 값으로 설정한다. 이유는 answers의 배열 길이가 길어질 경우를 대비하기 위해서이다. 두 가지 배열을 비교하며 두 배열의 요소가 같을 시 count를 증감시킨다.<br>
> 3.  증감시킨 conut배열을 비교하기 위해 for문을 활용한다. 이 때 또 다시 if문을 활용하여 조건을 삽입하는데 조건은 conut배열의 각 요소가 conut의 최대값과 같을 경우 answer에 해당 index+1을 push시키는 것이다. 이 때 +1을 하는 이유는 문제의 return이 최소 1부터 시작하기 때문이다. (1번째 수포자, 2번째 수포자, 3번째 수포자 중 정답이 가장 많은 수포자 출력) 또 최대값을 반환하는 Math.max() 함수에서 파라미터에 ...count(스프레드연산자)가 활용되었는데 이유는 count와 같이 스프레드연산자를 활용하지 않고 배열로 삽입 시 Number타입이 아니기때문에 NaN을 출력하기 때문이다. 그러므로 스프레드연산자를 활용하여 배열을 펼쳐준다.<br>
> 4.  push된 answer을 출력한다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
const answers = [1, 3, 2, 4, 2];

function solution2(answers) {
  const answer = [];
  const mathGiver1 = [1, 2, 3, 4, 5];
  const mathGiver2 = [2, 1, 2, 3, 2, 4, 2, 5];
  const mathGiver3 = [3, 3, 1, 1, 2, 2, 4, 4, 5, 5];

  const mathGiver1Count = answers.filter(
    (a, i) => a === mathGiver1[i % mathGiver1.length]
  ).length;
  const mathGiver2Count = answers.filter(
    (a, i) => a === mathGiver2[i % mathGiver2.length]
  ).length;
  const mathGiver3Count = answers.filter(
    (a, i) => a === mathGiver3[i % mathGiver3.length]
  ).length;
  const max = Math.max(mathGiver1Count, mathGiver2Count, mathGiver3Count);

  if (mathGiver1Count === max) answer.push(1);
  if (mathGiver2Count === max) answer.push(2);
  if (mathGiver3Count === max) answer.push(3);

  return answer;
}

console.log(solution2(answers));
```

### - 문제해설

> 1.  filter()메서드를 활용하여 정답이 들어있는 배열 answers의 배열요소와 mathGiver배열 요소를 비교한다. 두 배열 요소를 비교하여 같을 경우 새로운 배열로 반환하고 새롭게 반환한 배열의 length를 반환하여 정답의 갯수를 할당한다.<br>
> 2.  max변수에 Math.max()함수를 활용하여 파라미터로 정답의 갯수를 할당한 변수들을 비교하여 최대 정답 갯수를 할당한다.<br>
> 3.  조건문을 활용하여 각 수포자가 맞춘 정답의 갯수가 최대 갯수와 같을 경우 해당 수포자가 몇번째 수포자인지를 answer에 push한다.<br>
> 4.  push된 answer을 출력한다.

<br>

## (3) 참고자료

1. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/filter" target='_blank'>Array.prototype.filter()</a>
