# [Algorithm-SQL] 프로그래머스 - SUM, MAX, MIN - 최솟값 구하기

2023년 12월 29일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/59038

<br>
<br>

# 2. 나의 풀이

```sql

SELECT MIN(DATETIME) FROM ANIMAL_INS
```

1. SELECT `MIN`(DATETIME) FROM ANIMAL_INS : ANIMAL_INS 테이블의 DATETIME 컬럼을 조회하는데 MIN 함수를 사용하여 가장 작은 DATETIME 컬럼의 데이터를 조회한다.

<br>
<br>

# 3. 후기

저번 최댓값을 구할 때 사용했던 MAX 함수와 마찬가지로 최솟값을 구하기 위해 MIN을 사용하였다. 문제의 요구사항이 동물 보호소에 가장 먼저 들어온 동물이므로 최솟값을 의미하기 때문에 MIN을 사용하였다.

<br>
