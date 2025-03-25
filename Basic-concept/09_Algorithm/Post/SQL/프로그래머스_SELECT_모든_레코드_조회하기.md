# [Algorithm-SQL] 프로그래머스 - SELECT - 모든 레코드 조회하기

2025년 03월 25일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/59034

<br>
<br>

# 2. 나의 풀이

```sql
SELECT * FROM ANIMAL_INS
ORDER BY ANIMAL_ID ASC
```

1. ANIMAL_INS 테이블의 모든 컬럼을 조회한다
2. 정렬은 ORDER BY를 통해 ANIMAL_ID를 기준으로 오름차순 정렬하였다.

<br>
<br>

# 3. 후기

- 테이블 조회 시 모든 컬럼을 조회하는 경우 와일드 카드(`*`)를 사용할 수 있다.
