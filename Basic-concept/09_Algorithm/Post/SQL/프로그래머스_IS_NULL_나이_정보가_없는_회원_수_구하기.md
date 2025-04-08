# [Algorithm-SQL] 프로그래머스 - IS NULL - 나이 정보가 없는 회원 수 구하기

2025년 04월 08일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/131528

<br>
<br>

# 2. 나의 풀이

```sql
SELECT COUNT(*) AS USERS FROM USER_INFO
WHERE AGE IS NULL;
```

1. USER_INFO 테이블의 모든 컬럼을 조회한다. 이 때 COUNT를 활용하여 조회된 행의 개수를 센다. 최종 결과는 USERS라는 이름의 컬럼으로 반환해야하기 때문에 AS를 활용하여 컬럼에 별칭을 지정한다.
2. age 컬럼이 null인 경우만 조회해야하므로 WHERE과 IS NULL을 활용하여 null인 행을 찾는다.
3. 최종적으로 USERS 컬럼에 age가 null인 행의 개수를 반환한다.

<br>
<br>

# 3. 후기

- `COUNT` : 행의 개수를 센다.
- `AS` : 별칭을 지정한다.

<br>
