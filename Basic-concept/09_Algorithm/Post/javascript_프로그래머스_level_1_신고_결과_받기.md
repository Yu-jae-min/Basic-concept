# **[Algorithm] 프로그래머스 Level 1 - 신고 결과 받기**

2023년 08월 24일

<br>

## **1. 문제**

- https://school.programmers.co.kr/learn/courses/30/lessons/92334

<br>
<br>

## **2. 나의 풀이**

```tsx
const mySolution = (id_list, report, k) => {
  var answer = [...id_list];

  const filterDuplicateReportArray = [...new Set(report)];
  const idListObject = Object.fromEntries(
    id_list.map((reportData) => {
      const [repoter, _] = reportData.split(" ");
      return [repoter, 0];
    })
  );

  const reportCount = { ...idListObject };
  const resultMailCount = { ...idListObject };

  filterDuplicateReportArray.forEach((reportData) => {
    const [_, targetUser] = reportData.split(" ");

    reportCount[targetUser] = reportCount[targetUser] + 1;
  });

  filterDuplicateReportArray.forEach((reportData) => {
    const [reportUser, targetUser] = reportData.split(" ");

    if (reportCount[targetUser] >= k)
      resultMailCount[reportUser] = resultMailCount[reportUser] + 1;
  });

  return answer.map((id) => resultMailCount[id]);
};

console.log(
  mySolution(
    ["muzi", "frodo", "apeach", "neo"],
    ["muzi frodo", "apeach frodo", "frodo neo", "muzi neo", "apeach muzi"],
    2
  )
); // [2, 1, 1, 0]
```

1. 최종 출력 값은 순서가 id_list와 순서가 동일해야하므로 순서가 있는 배열을 활용하기 위해 스프레드 문법으로 id_list를 answer 변수를 복사했다.
2. `filterDuplicateReportArray` 변수에 동일한 신고 내용을 제거하기 위해 `Set 생성자 함수`를 사용하여 중복 값을 제거하였다.
3. 신고 횟수와 메일 횟수를 id 별로 카운트 하기 위한 객체를 생성하기 위해 `idListObject` 변수에 배열을 key, value로 반환하는 `fromEntries 메소드`를 활용하여 객체를 생성하였다. 그 후 `reportCount`, `resultMailCount` 변수에 스프레드 문법을 통해 복제하였다.
4. 신고 내용인 `filterDuplicateReportArray` 배열을 반복문으로 돌리는데 반복문 내부에서 구조 분해 후 신고 횟수를 카운트하는 `reportCount` 객체 내부에 id를 가리키는 key와 현재 사이클의 신고 당한 유저에 id를 매핑하여 증가시켰다.
5. 신고 내용인 `filterDuplicateReportArray` 배열을 반복문으로 돌리는데 반복문 내부에서 구조 분해 후 메일 횟수를 카운트하는 `resultMailCount` 객체 내부에 id를 가리키는 key와 현재 사이클의 신고 당한 유저에 id를 매핑하여 증가시켰다. 이 때 카운트를 증가시키는 조건이 있는데 구조 분해한 배열 요소 중 신고 당한 유저의 신고 당한 횟수가 k 이상인 경우 신고한 유저의 안내 메일 횟수 카운트를 증가시켰다.
6. 최종 값을 출력하기 위해 id_list 파라미터가 복제된 id 리스트가 담긴 배열 answer을 map으로 돌려 변환하는데 이 때 안내 메일 횟수로 변환하여야 하기 때문에 resultMailCount 객체의 key와 매핑시켜 변환하였다.

<br>
<br>

## **3. 인기 풀이**

```tsx
const othersSolution = (id_list, report, k) => {
  let reports = [...new Set(report)].map((a) => {
    return a.split(" ");
  });

  let counts = new Map();

  for (const bad of reports) {
    counts.set(bad[1], counts.get(bad[1]) + 1 || 1);
  }

  let good = new Map();

  for (const report of reports) {
    if (counts.get(report[1]) >= k) {
      good.set(report[0], good.get(report[0]) + 1 || 1);
    }
  }

  let answer = id_list.map((a) => good.get(a) || 0);

  return answer;
};

console.log(
  othersSolution(
    ["muzi", "frodo", "apeach", "neo"],
    ["muzi frodo", "apeach frodo", "frodo neo", "muzi neo", "apeach muzi"],
    2
  )
); // [2, 1, 1, 0]
```

1. `reports` 변수에 동일한 신고 내용을 제거하기 위해 `Set 생성자 함수`를 사용하여 중복 값을 제거하였다. 그 후 map으로 돌려 신고자, 신고대상을 배열 형태로 변환하였다. (ex: `[[신고자, 신고대상], [신고자, 신고대상]]`)
2. `counts` 변수에 신고 횟수를 카운트하기 위해 `Map 생성자 함수`를 통해 key, value를 저장할 수 있는 Map 객체를 생성하였다.
3. counts 변수 생성 후 `for of`로 중복 값을 제거한 신고 내용 배열 reports을 기준으로 반복하였는데 이 때 `set 메소드`를 활용하여 Map 객체 내부에 값을 할당하였다. 할당되는 값의 key는 현재 순환되는 배열 요소 중 index 1의 값이 신고 대상의 id 이므로 현재 배열 요소 index 1의 값을 key로 활용하였고 value는 기존 값을 get 메소드로 우선 가져온 뒤 그 값에 1을 누적하여 더하였다. 만약 기존 값이 없다면 1을 할당하였다.
4. `good` 변수에 메일 횟수를 카운트하기 위해 `Map 생성자 함수`를 통해 key, value를 저장할 수 있는 Map 객체를 생성하였다.
5. good 변수 생성 후 for of로 중복 값을 제거한 신고 내용 배열 reports을 기준으로 반복하였는데 이 때 `set 메소드`를 활용하여 Map 객체 내부에 값을 할당하였다. 할당되는 값의 key는 현재 순환되는 배열 요소 중 index 0의 값이 신고자의 id 이므로 현재 배열 요소 index 0의 값을 key로 활용하였고 value는 기존 값을 get 메소드로 우선 가져온 뒤 그 값에 1을 누적하여 더하였다. 만약 기존 값이 없다면 1을 할당하였다. 이 때 카운트를 증가시키는 조건이 있는데 이전에 신고 횟수를 카운트한 counts Map 객체 내부에 신고 대상의 값이 k 이상인 경우 신고자에게 안내해야 할 메일 횟수 카운트를 증가시켰다.
6. 최종 값을 출력하기 위해 전체 유저 아이디를 담은 배열 `id_list`를 map으로 돌려 변환하는데 이 때 안내 메일 카운트를 위해 생성한 Map 객체 `good`에 값을 `get 메소드`로 가져올 때 현재 배열 요소, 즉 유저 id를 활용하여 good 객체의 value로 가져와 변환하였다.

<br>
<br>

## **4. 비교**

나의 풀이와 인기 풀이를 비교해보았을 때 전체적인 문제 풀이 방식은 비슷했다. 우선 동일한 유저가 동일한 유저를 다시 신고하는 중복 신고는 불가하기 때문에 Set 함수를 통해 신고 내용의 중복을 제거하였고 그 후 각 유저가 신고 당한 횟수, 각 유저에게 안내 메일을 발송해야하는 횟수를 카운트하였다. 이 때 카운트하는 방법에서 차이가 있었는데 나의 풀이의 경우 객체 생성 후 forEach 메소드로 순회하며 카운트하였고 인기 풀이의 경우 Map 생성자 함수로 Map 객체 생성 후 for of로 순회하며 카운트하였다. 개인적으로는 두 풀이가 크게 차이가 난다고 생각하지는 않았다. 하지만 코드 길이나 가독성을 보았을 때 인기 풀이가 더 좋은 코드인 것 같다. 그래도 해당 문제의 정답률이 36% 밖에 되지 않았는데 한방에 모든 케이스를 통과한 것이 매우 매우 뿌듯하다. 물론 운이겠지만..ㅎㅋ

<br>
