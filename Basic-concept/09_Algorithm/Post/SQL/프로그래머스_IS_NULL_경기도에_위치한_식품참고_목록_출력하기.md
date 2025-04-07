# [Algorithm-SQL] 프로그래머스 - IS NULL - 경기도에 위치한 식품창고 목록 출력하기

2025년 04월 07일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/131114

<br>
<br>

# 2. 나의 풀이

```sql
SELECT WAREHOUSE_ID, WAREHOUSE_NAME, ADDRESS,
IF(FREEZER_YN IS NULL, 'N', FREEZER_YN)
FROM FOOD_WAREHOUSE
WHERE ADDRESS LIKE '경기도%'
ORDER BY WAREHOUSE_ID
```

1. FOOD_WAREHOUSE 테이블의 WAREHOUSE_ID, WAREHOUSE_NAME, ADDRESS, FREEZER_YN 컬럼을 조회한다. 이 때 냉동시설 여부(FREEZER_YN)가 null인 경우 N으로 치환해야하기 떄문에 IF절을 활용한다.
2. 특정 지역에 위치한 공장을 찾기 위해 WHERE절을 사용하고 이 때 경기도에 위치하는 공장을 찾기 위해 LINK 연산자를 활용하여 데이터를 찾는다.
3. WAREHOUSE_ID 기준으로 오름차순 정렬을 위해 ORDER BY로 정렬한다.

<br>
<br>

# 3. 후기

- 특정 조건을 통해 컬럼 데이터를 치환할 때 IF절을 활용할 수 있다.
  - IF(condition, true_val, false_val)

<br>
