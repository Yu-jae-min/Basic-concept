# [Algorithm-SQL] 프로그래머스 - SELECT - 아픈 동물 찾기

2025년 03월 26일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/59036

<br>
<br>

# 2. 나의 풀이

```sql
SELECT ANIMAL_ID, NAME
FROM ANIMAL_INS
WHERE INTAKE_CONDITION = 'Sick'
```

1. ANIMAL_INS 테이블의 ANIMAL_ID, NAME 컬럼을 조회한다.
2. 아픈 동물을 찾기 위해 정렬은 WHERE절을 통해 INTAKE_CONDITION 컬럼의 데이터가 Sick인 데이터를 찾는다.

<br>
<br>

# 3. 후기

- 쉬운 문제였다. WHERE절에 조건 하나만 추가하였다.

<br>
