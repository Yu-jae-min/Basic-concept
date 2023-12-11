# [javascript-algorithm] 프로그래머스 - 완주하지 못한 선수

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/42576" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/42576</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
const participant1 = ["marina", "josipa", "nikola", "vinko", "filipa"];
const completion1 = ["josipa", "filipa", "marina", "nikola"];

function solution1(participant, completion) {
  participant.sort();
  completion.sort();

  for (let i = 0; i < participant.length; i++) {
    if (participant[i] != completion[i]) return participant[i];
  }
}

console.log(solution1(participant1, completion1)); // vinko
```

### - 문제해설

> 1.  sort()메서드로 각 비교할 각 배열을 오름차순으로 정렬한다.<br>
> 2.  for문으로 참가자 변수 participant보다 작을 때까지 반복하며 participant와 completion의 배열 요소를 순서대로 비교하며 같지 않을 경우의 배열 요소를 리턴한다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
const participant2 = ["leo", "kiki", "eden"];
const completion2 = ["eden", "kiki"];

function solution2(participant, completion) {
  completion.map((name) => (completion[name] = (completion[name] | 0) + 1));
  // completion : ['eden', 'kiki', eden: 1, kiki: 1]
  return participant.find((name) => !completion[name]--);
  // completion : ['eden', 'kiki', eden: 1, kiki: 1, leo: NaN]
}

console.log(solution2(participant2, completion2)); // leo
```

### - 문제해설

> 1.  completion.map()을 활용하여 completion[name]을 할당한다. 배열은 typeof로 확인해보면 객체이다. 그러므로 key-value페어를 저장할 수 있다. 여기서 completion[name]는 key-value페어가 되고 여기에 1을 더해주며 value값을 할당한 것이다. name은 completion에 각 인수이며 예를 들어 "eden"에 맵함수가 실행된다면 eden이라는 key에 value값을 할당한 것이 추가되는 것이다. 또한 이름이 중복으로 들어가는 경우가 있기 때문에 논리연산자 |를 통해 key-value페어가 이미 존재하는지 확인 후 존재한다면 이름이 중복이라는 뜻이기 때문에 기존 value값에 1을 더하고, 이름이 하나만 존재하는 경우 undefined가 되므로 0을 출력하도록 하며 0에 1을 더한다. completion.map() 실행 후에 콘솔로 확인해보면 ['eden', 'kiki', eden: 1, kiki: 1]가 출력되며 key-value페어값이 추가되어 해당 이름의 갯수가 담긴 것을 확인할 수 있다.<br>
> 2.  participant에 find()메서드가 실행되며 기존 배열들을 불러온 후 해당 함수 조건을 만족하는 첫번째 값을 리턴한다. 이 때 조건 중 증감연산자는 후위연산자이기 때문에 !을 통해 참,거짓(false, 0, -0, NaN, null, undefined, '')을 판별한 후 그 열의 계산이 다 끝나고 다음 열로 갈 때 값이 바뀌게 된다. 즉 불러온 순간의 값으로 참 거짓을 판별하는 것이다. participant이 불려오며 completion에 해당 이름이 몇 개 존재했었는지를 판별하게 되고 이름이 1개인 경우나 1개 이상인 경우 불리언으로 보면 참이지만 !을 통해 거짓이 된다. 즉 name에 해당하는 페어가 completion에 존재하지 않을 때 undefined를 리턴하게 되고 불리언으로 보면 거짓이지만 !을 통해 참이 되므로 해당 값을 출력하게 되는 것이다.<br>
> 3.  추가로 0을 리턴하는 경우에는 동명의 참가자가 2명 이상 있었는데 그 중 1명이 안들어왔을 때이고, undefined를 리턴하게 되는 경우는 못들어온 이름이 1개 뿐이었고 그 사람이 못들어왔을 때이다. 또한 undefined에 !를 붙이고 후위연산자 --를 붙여주면 해당 key-value 페어가 존재하게 되고, 값은 NaN이 된다.

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
const participant3 = ["mislav", "stanko", "mislav", "ana"];
const completion3 = ["stanko", "ana", "mislav"];

function solution3(participant, completion) {
  const completer = completion.reduce(
    (acc, cur) => ((acc[cur] = acc[cur] ? acc[cur] + 1 : 1), acc),
    {}
  );
  // {stanko: 1, ana: 1, mislav: 1}

  return participant.find((t) => {
    if (completer[t]) completer[t] = completer[t] - 1;
    else return true; // {stanko: 0, ana: 1, mislav: 0}
  });
}

console.log(solution3(participant3, completion3)); // mislav
```

### - 문제해설

> 1.  reduce()메서드를 통해 배열의 각 요소에 value값을 추가한다. 누산기와 현재값을 인자로 가지며 실행문에서는 누산기의 value와 현재값의 value를 비교하여 중복되는 이름의 여부를 확인한다. 중복되는 이름이 없는 경우 false가 되므로 해당 value에 1을 할당한다. 또한 중복되는 이름이 있는 경우 false의 과정을 거쳐 이미 value가 할당된 상태이므로 그 값에 1을 더하게 된다. reduce()메서드가 종료된 후에는 객체의 key,value페어가 존재하게 된다. {stanko: 1, ana: 1, mislav: 1}<br>
> 2.  find()메서드를 통해 불리언이 true인 경우 첫번째 값을 출력하게 되는데 if문을 활용하여 조건문을 생성한다. 조건은 value의 존재 여부가 되며 value가 존재한다면 -1을 해주고 이 값은 존재하지 않은 경우 true를 통해 value가 비어있는 배열 요소를 출력한다. 디버깅해보면 completer는 {stanko: 0, ana: 1, mislav: 0}가 되는데 중복되는 mislav가 리턴되며 종료되기 때문에 ana는 그대로 1의 value를 가지게 된다.

<br>

## (3) 참고자료

1. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/find" target='_blank'>Array.prototype.find()</a><br>
2. <a href="https://niceman.tistory.com/79" target='_blank'>Array.prototype.reduce()</a>
