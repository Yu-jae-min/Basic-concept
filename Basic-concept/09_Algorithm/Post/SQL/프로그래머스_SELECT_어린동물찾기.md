# [Algorithm-SQL] 프로그래머스 - SELECT - 어린동물찾기

2023년 12월 12일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/59037

<br>
<br>

# 2. 나의 풀이

```sql
SELECT ANIMAL_ID, NAME
FROM ANIMAL_INS
WHERE INTAKE_CONDITION != 'Aged'
ORDER BY ANIMAL_ID ASC;
```

1. FROM : ANIMAL_INS 테이블을 조회한다.
2. SELECT : ANIMAL_ID, NAME 테이블을 조회한다.
3. WHERE : 어린동물은 INTAKE_CONDITION 테이블의 값이 Aged가 아닌 경우이기 때문에 조건을 추가한다.
4. ORDER BY : ID순으로 조회하기 위해 ANIMAL_ID를 기준으로 정렬하는데 오름차순 ASC 기준으로 정렬한다.

<br>
<br>

# 3. 후기

첫 SQL 풀이다. 매일 javascript 알고리즘만 풀다가 새로운 언어를 작성해보니 재밌다.

<br>
