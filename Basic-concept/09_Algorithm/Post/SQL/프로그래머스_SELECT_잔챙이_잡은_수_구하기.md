# [Algorithm-SQL] 프로그래머스 - SELECT - 잔챙이 잡은 수 구하기

2025년 05월 13일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/293258

<br>
<br>

# 2. 나의 풀이

```sql
-- 코드를 작성해주세요
SELECT COUNT(*) AS FISH_COUNT FROM FISH_INFO
WHERE LENGTH IS NULL;
```

1. FISH_INFO 테이블을 조회한다. 물고기 카운트를 세기 위해 `COUNT`를 활용한다. 그 후 `IS NULL`을 통해 LENGTH가 NULL인 경우를 확인하여 10cm 이하 물고기를 찾는다. 최종적으로 컬럼명은 FISH_COUNT가 되므로 별칭을 지정한다.

<br>
<br>

# 3. 후기

- `IS NULL` : 컬럼 값이 NULL인 경우를 확인한다.

<br>
