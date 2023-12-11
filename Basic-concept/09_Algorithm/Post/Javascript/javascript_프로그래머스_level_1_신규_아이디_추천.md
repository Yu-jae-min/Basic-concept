# **[Algorithm] 프로그래머스 Level 1 - 신규 아이디 추천**

2023년 08월 12일

<br>
<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/72410

<br>
<br>

## **2. 나의 풀이**

```tsx
const mySolution = (numbers, hand) => {
  const step1 = new_id.toLowerCase();

  const step2 = step1
    .split("")
    .filter((str) => /[a-z_\-\.\d]/g.test(str))
    .join("");

  const step3 = step2
    .split("")
    .filter((str, idx, arr) => str !== "." || str !== arr[idx + 1])
    .join("");

  const step4 = step3
    .split("")
    .filter((str, idx, arr) => {
      const checkIdx = idx === 0 || idx === arr.length - 1;
      const checkDote = str === ".";

      return !(checkDote && checkIdx);
    })
    .join("");

  const step5 = step4 || "a";

  let step6 = step5.length >= 16 ? step5.slice(0, 15) : step5;
  if (step6[step6.length - 1] === ".") step6 = step6.slice(0, step6.length - 1);

  const step7 =
    step6.length <= 2
      ? step6 + step6[step6.length - 1].repeat(3 - step6.length)
      : step6;

  return step7;
};

console.log(mySolution("...!@BaT#*..y.abcdefghijklm")); // bat.y.abcdefghi
```

1. 1단계에서 toLowerCase 메소드를 사용하여 소문자로 치환하였다.
2. 2단계에서 filter 메소드로 순회하며 정규식을 활용하여 `소문자`, `_`, `-`, `.` 의 문자만 허용되도록 필터 처리 하였다.
3. 3단계에서 filter 메소드로 순회하며 해당 문자의 다음 index의 문자가 자신과 같지 않은 경우의 문자만 출력되도록 필터 처리 하였다.
4. 4단계에서 filter 메소드로 순회하며 index가 0, 즉 처음 문자나 index가 마지막, 즉 마지막 문자가 `.`인 경우 필터 처리 하였다.
5. 5단계에서 해당 문자가 공백인 경우 or 연산자를 활용하여 a 문자로 치환하였다.
6. 6단계에서 해당 문자가 16자 이상인 경우 slice 메소드로 잘라내었고 잘라낸 후 마지막 문자가 `.`인 경우 slice 메소드로 한번 더 잘라내었다.
7. 7단계에서 해당 문자가 2자 이하가 아닌 경우 그대로 출력하였고 2자 이하인 경우 해당 문자에 해당 문자 끝 자리를 3자리가 될 때 까지 repeat 메소드를 사용하여 반복한 뒤 더해주어 출력하였다.

<br>
<br>

## **3. 인기 풀이**

```tsx
const othersSolution = (numbers, hand) => {
  const answer = new_id
    .toLowerCase() // 1
    .replace(/[^\w-_.]/g, "") // 2
    .replace(/\.+/g, ".") // 3
    .replace(/^\.|\.$/g, "") // 4
    .replace(/^$/, "a") // 5
    .slice(0, 15)
    .replace(/\.$/, ""); // 6
  const len = answer.length;
  return len > 2 ? answer : answer + answer.charAt(len - 1).repeat(3 - len);
};

console.log(othersSolution("...!@BaT#*..y.abcdefghijklm")); // bat.y.abcdefghi
```

1. 1단계에서 나와 같은 방식으로 소문자 치환하였다.
2. 2단계에서 word를 표현하는 표현식 `w`를 사용하여 알파벳, 숫자, `_`를 표현하였고 `-`, `_`, `.` 등을 추가하여 허용되지 않은 문자를 공백으로 치환하였다.
3. 3단계에서 반복 문자를 나타내는 `+` 표현식을 사용하여 반복되는 `.` 문자를 하나의 `.` 문자로 치환하였다.
4. 4단계에서 문자열의 시작을 알리는 `^x`, 문자열의 끝을 알리는 `x$` 표현식을 사용하여 양 끝 `.` 문자를 공백으로 치환하였다.
5. 5단계에서 문자열의 시작을 알리는 `^x`, 문자열의 끝을 알리는 `x$` 표현식을 사용하여 문자가 비어있는 문자인 경우 `a` 로 치환하였다.
6. 6단계에서 해당 문자가 15자를 초과하는 경우 slice 메소드를 통해 15자리까지 잘라낸 후 문자열의 마지막을 알리는 `x$` 표현식을 사용하여 마지막 문자가 `.` 인 경우 공백으로 치환하였다.
7. 마지막 7단계를 출력할 때 6단계를 거친 문자가 2자를 초과하는 경우 해당 문자를 출력하고 2자를 초과하지 않는 경우 해당 charAt을 통해 해당 문자의 마지막 문자를 구한 뒤 repeat를 통해 해당 문자를 반복하여 기존 문자에 더하였다.

<br>
<br>

## **4. 비교**

나의 풀이와 인기 풀이의 차이점은 일단 코드 길이에서 엄청난 차이가 발생했다. 인기 풀이의 경우 대부분의 풀이를 `replace` 메소드와 정규식을 활용하여 치환하였다. 반면 나의 풀이의 경우 해당 문자를 배열로 변환한 뒤 `filter` 메소드를 사용하고 다시 `join` 메소드를 합쳐주는 방식으로 작업하였다. 이렇게 작업하다 보니 코드 길이가 매우 길어지게 되었다. 정규식은 모르는 부분이 많았기 때문에 인기 풀이의 코드를 해석해보며 조금이나마 얻어가는 것이 있었다. 위 코드를 보며 정규식을 필요한 때에 적절히 사용하면 코드 길이를 획기적으로 줄일 수 있고 가독성을 높일 수 있음을 알 수 있었다.

<br>
