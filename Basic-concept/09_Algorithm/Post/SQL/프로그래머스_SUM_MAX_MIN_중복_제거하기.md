# [Algorithm-SQL] 프로그래머스 - SUM, MAX, MIN - 중복 제거하기

2024년 01월 02일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/59408

<br>
<br>

# 2. 나의 풀이

```sql
SELECT COUNT(DISTINCT NAME) FROM ANIMAL_INS
WHERE NAME IS NOT NULL
```

1. SELECT COUNT(DISTINCT NAME) FROM ANIMAL_INS : ANIMAL_INS 테이블의 NAME 컬럼 레코드를 조회한다. 이 때 중복을 제거하기 위해 DISTINCT를 활용한다. 중복을 제거한 후 COUNT 함수를 통해 유니크한 동물의 이름을 세어 반환한다.
2. WHERE NAME IS NOT NULL : WHERE을 통해 조건부로 컬럼의 레코드를 조회하는데 조건은 NULL이 아닌 경우를 조건으로 설정한다.

<br>
<br>

# 3. 후기

`DISTINCT`와 `IS NOT NULL`에 대해 알 수 있었다.

- `DISTINCT` : 지정한 컬럼의 고유한 레코드만 반환한다. 즉 레코드의 중복을 제거한다. 주의할 점은 여러 컬럼을 한 번에 지정할 때 개별로 지정할 수 없다는 특징이 있다.
- `IS NOT NULL` : IS NOT NULL 연산자는 값이 비어있지 않은 경우, 즉 값이 있는 경우를 나타낸다. 반면 IS NULL 연산자는 값이 없는 경우를 나타낸다.

<br>
