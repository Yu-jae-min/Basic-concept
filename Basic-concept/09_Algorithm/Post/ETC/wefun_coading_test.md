# [Algorithm] 위펀(Wefun) 코딩테스트

2023년 12월 12일

<br>

# 1번 문제

## 문제

![wefun_01_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/e8eaa88d-93c7-42e0-bd9d-9475fa30b090)

![wefun_01_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/1f1bc499-3700-44d1-9152-d2068f3fd45c)

![wefun_01_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/7d0f3c44-57d6-4b3f-a8c0-50098099a065)

## 풀이

```js
const One = (day, k) => {
  const answer = [];
  const month = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31];
  let base = day + k - 1;

  month.forEach((_, i, arr) => {
    if (i != 0) base += arr[i - 1];

    const isWeekend = Number(base % 7 >= 5);
    answer.push(isWeekend);
  });

  return answer;
};

console.log(One(6, 25)); // [1, 0, 0, 1, 0, 0, 1, 0, 0, 1, 0, 0]
```

<br>
<br>

# 2번 문제

## 문제

![wefun_02_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/ea165af5-598d-4ace-bc67-6d43bf4364a3)

![wefun_02_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/612227fa-ef22-49e4-81b5-65c6bee3efe9)

![wefun_02_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/f45c1510-2db9-442d-903e-318c44deb5d9)

## 풀이

```js
const Two = (orders) => {
  const result = [];
  const list = {};
  let maxValue = 0;

  orders.forEach((order) => {
    [name, ...foods] = order.split(" ");
    list[name] = [];
  });

  orders.forEach((order) => {
    [name, ...foods] = order.split(" ");
    foods.forEach((food) => list[name].push(food));
  });

  const foodsCount = Object.entries(list)
    .map(([name, foods]) => [name, [...new Set(foods)].length])
    .sort((a, b) => b[1] - a[1]);

  for (let i = 0; i < foodsCount.length; i++) {
    if (!(maxValue === 0 || maxValue === foodsCount[i][1])) break;

    maxValue = foodsCount[i][1];
    result.push(foodsCount[i][0]);
  }

  return result;
};

console.log(
  Two([
    "a pizza pasta",
    "a pizza pizza",
    "a noodle",
    "b pasta",
    "b noodle sandwich pasta",
    "b steak noodle",
  ])
); // [1, 2, 4, 2]
```

<br>
<br>

# 3번 문제

## 문제

![wefun_03_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/722d8388-4852-4d9a-9668-5cfa2b6f603b)

![wefun_03_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/d2c0b63d-cf10-4640-954a-9861bdc43138)

## 풀이

```js
const Three = (prices) => {
  const answer = new Array(prices.length).fill(1);

  for (let i = 0; i < prices.length; i++) {
    for (let j = 0; j < prices.length; j++) {
      if (i === j) continue;

      if (prices[i] < prices[j]) answer[i] += 1;
    }
  }

  return answer;
};

console.log(Three([3, 2, 1, 2])); // [1, 2, 4, 2]
```

<br>
<br>

# 4번 문제

## 문제

![wefun_04_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/dc6e564d-2ba9-4def-bf47-30bc7f7d7e74)

![wefun_04_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/fe2672f8-c315-464f-98b7-beef7651079a)

![wefun_04_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/8be692e5-f687-4370-9c1e-6ca5f4564235)

![wefun_04_04](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/85597435-3d52-4340-9456-74b2daf0a615)

![wefun_04_05](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/559235a3-92d2-4eef-9f2f-82bd61a27db0)

## 풀이

```js
const Four = (N, relation, dirname) => {
  var answer = 0;
  // answer = "root/cs/solution".length;

  return answer;
};

const a4 = 7;
const b4 = [
  [1, 2],
  [2, 5],
  [2, 6],
  [1, 3],
  [1, 4],
  [3, 7],
];
const c4 = ["root", "abcd", "cs", "hello", "etc", "hello", "solution"];
console.log(Four(a4, b4, c4)); // 16
```

<br>
