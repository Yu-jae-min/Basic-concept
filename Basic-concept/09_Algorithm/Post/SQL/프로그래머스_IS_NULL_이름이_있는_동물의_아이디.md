# [Algorithm-SQL] 프로그래머스 - IS NULL - 이름이 있는 동물의 아이디

2025년 03월 27일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/59407

<br>
<br>

# 2. 나의 풀이

```sql
SELECT ANIMAL_ID FROM ANIMAL_INS
WHERE NAME IS NOT NULL
ORDER BY ANIMAL_ID ASC
```

1. ANIMAL_INS 테이블의 ANIMAL_ID 컬럼을 조회한다.
2. 이름이 있는 동물의 아이디를 찾기 위해 WHERE절을 사용하고 이름이 null이 아닌 경우를 찾아야하기 때문에 NAME IS NOT NULL을 조건으로 데이터를 찾는다.
3. ANIMAL_ID 기준으로 오름차순 정렬을 위해 ORDER BY ~ ASC로 정렬한다.

<br>
<br>

# 3. 후기

- WHERE절 내부에서 IS NOT 사용 시 NOT을 통해 NULL이 아닌 컬럼을 찾을 수 있다.

<br>
