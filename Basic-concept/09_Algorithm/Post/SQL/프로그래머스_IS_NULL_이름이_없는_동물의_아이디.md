# [Algorithm-SQL] 프로그래머스 - IS NULL - 이름이 없는 동물의 아이디

<br>

2025년 03월 24일

# 1. 문제

- [https://school.programmers.co.kr/learn/courses/30/lessons/131532](https://school.programmers.co.kr/learn/courses/30/lessons/59039)

<br>
<br>

# 2. 나의 풀이

```sql
SELECT ANIMAL_ID
FROM ANIMAL_INS
WHERE NAME is null
ORDER BY ANIMAL_ID ASC
```

1. ANIMAL_INS 테이블에 ANIMAL_ID을 조회한다.
2. WHERE 절을 통해 조건을 걸었다. 조건은 NAME 컬럼의 값이 null인 경우를 조회하였다.
3. 정렬은 ORDER BY를 통해 오름차순 정렬하였다.

<br>
<br>

# 3. 후기

- Null을 판별하는 is Null에 대해서 배울 수 있었다.
- `~ is Null`
  - 해당 컬럼의 값이 null(값이 없다, 정의되어 있지 않다, 비어있다)인지 판별한다.

<br>
