# [javascript-algorithm] 프로그래머스 - 이상한 문자 만들기

## (1) 문제링크

<a href="https://programmers.co.kr/learn/courses/30/lessons/12930" target='_blank'>https://programmers.co.kr/learn/courses/30/lessons/12930</a>

<br>

## (2) 문제풀이 및 해설 1

### - 문제풀이

```javascript
let n = "try hello world";

function solution1(n) {
  return n
    .split(" ")
    .map((word) => {
      let result = "";
      for (let i = 0; i < word.length; i++) {
        if (i % 2) {
          result += word[i].toLowerCase();
        } else {
          result += word[i].toUpperCase();
        }
      }
      return result;
    })
    .join(" ");
}

console.log(solution1(n)); // TrY HeLlO WoRlD
```

### - 문제해설

> 1.  문자열을 split()메서드로 공백을 기준으로 잘라 배열로 만든다.<br>
> 2.  map()메서드로 잘라준 배열 각각의 조건을 개별로 적용시켜준다. result변수라는 빈 문자열을 담은 변수를 만든 뒤 for문을 이용한다. 조건은 해당 문자열을 length보다 작을 경우 조건문을 반복한다. for문 안에는 if문의 i%2 연산을 이용하여 값이 1일 경우 true, 0일 경우 false인 것을 활용하여 홀짝을 나누고 소문자 혹은 대문자로 변환하여 result변수에 더한다.<br>
> 3.  join()메서드로 나누어져있는 배열들을 하나의 문자로 합쳐준다.

<br>

## (2) 문제풀이 및 해설 2

### - 문제풀이

```javascript
let n = "try hello world";

function solution2(n) {
  return n
    .split(" ")
    .map((i) =>
      i
        .split("")
        .map((j, key) => (key % 2 === 0 ? j.toUpperCase() : j))
        .join("")
    )
    .join(" ");
}

console.log(solution2(n)); // TrY HeLlO WoRlD
```

### - 문제해설

> 1.  문자열을 split()메서드로 공백을 기준으로 잘라 배열로 만든다.<br>
> 2.  map()메서드를 활용하여 잘려진 배열을 다시 한번 잘라 각각의 문자값을 가져올 수 있도록한다. 그 후 map()메서드를 중첩으로 사용하여 각각의 문자값을 변환한다. 이 때 조건은 삼항연산자를 활용하는데 key%2 연산을 이용하여 값이 1일 경우 true, 0일 경우 false인 것을 활용하여 홀짝을 나누고 소문자 혹은 대문자로 변환한다.<br>
> 3.  개별로 나뉘어져있는 문자를 join()메서드를 활용하여 하나의 단어로 합쳐준다. (ex "t","r","y" -> "try")<br>
> 4.  map()메서드 종료 후 단어로 나뉘어져있는 문자를 join()메서드를 활용하여 하나의 문장으로 합쳐준다. (ex "try","hello" -> "try hello")

<br>

## (2) 문제풀이 및 해설 3

### - 문제풀이

```javascript
let n = "try hello world";

function solution3(n) {
  let str = "";
  let arr = n.split(" ");

  for (let i in arr) {
    for (let j = 0; j < arr[i].length; j++) {
      let t = arr[i][j];
      str += j % 2 === 0 ? t.toUpperCase() : t.toLowerCase();
    }
    str += " ";
  }
  return str.slice(0, str.length - 1);
}

console.log(solution3(n)); // TrY HeLlO WoRlD
```

### - 문제해설

> 1.  str변수에 빈 문자열을 할당하고, arr변수에 split()메서드로 공백을 기준으로 잘라 배열로 만들어 할당한다.<br>
> 2.  for in문을 활용한다. arr배열을 순회하는데 중첩으로 for문을 활용한다. for문은 단어의 length보다 작을 때 까지 반복한다. 변수 t에 각각의 문자를 할당 후 str변수에 홀수를 비교하여 더해준다. 삼항연산자를 이용하여 각각에 문자 index의 나머지를 활용하여 true와 false로 나누고 소문자 혹은 대문자로 변환한다.<br>
> 3.  사이클이 끝난 단어 사이에 공백을 넣어주기 위해 공백 문자열을 삽입한다.<br>
> 4.  정확하 문자의 출력값을 위해 slice()메서드를 활용하여 0번째부터 length-1까지의 문자를 출력한다.

<br>

## (3) 참고자료

1. <a href="https://squll1.tistory.com/entry/javascript-%EB%8C%80%EB%AC%B8%EC%9E%90-%EC%86%8C%EB%AC%B8%EC%9E%90-%EB%B3%80%ED%99%98" target='_blank'>toLowerCase() / toUpperCase()</a><br>
2. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/join" target='_blank'>join()</a><br>
3. <a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/slice" target='_blank'>slice()</a>
