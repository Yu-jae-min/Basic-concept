# [Algorithm-SQL] 프로그래머스 - SELECT - 역순 정렬하기

2025년 03월 26일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/59035

<br>
<br>

# 2. 나의 풀이

```sql
SELECT NAME, DATETIME
FROM ANIMAL_INS
ORDER BY ANIMAL_ID DESC
```

1. ANIMAL_INS 테이블의 NAME, DATETIME 컬럼을 조회한다
2. 정렬은 ORDER BY를 통해 ANIMAL_ID를 기준으로 내림차순 정렬하였다.

<br>
<br>

# 3. 후기

- 쉬운 문제였다. ORDER BY를 통해 역순으로 정렬만 하였다.

<br>
