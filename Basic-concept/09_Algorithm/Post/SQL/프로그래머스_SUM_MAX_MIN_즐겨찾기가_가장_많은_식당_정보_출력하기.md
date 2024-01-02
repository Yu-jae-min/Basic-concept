# [Algorithm-SQL] 프로그래머스 - SUM, MAX, MIN - 즐겨찾기가 가장 많은 식당 정보 출력하기

2024년 01월 03일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/131123

<br>
<br>

# 2. 나의 풀이

```sql
SELECT FOOD_TYPE, REST_ID, REST_NAME, MAX(FAVORITES) FROM REST_INFO
GROUP BY FOOD_TYPE
ORDER BY FOOD_TYPE DESC
```

1. SELECT FOOD_TYPE, REST_ID, REST_NAME, MAX(FAVORITES) FROM REST_INFO : REST_INFO 테이블의 FOOD_TYPE, REST_ID, REST_NAME, FAVORITES 컬럼을 조회하는데 MAX 함수를 사용하여 FAVORITES 컬럼 레코드의 최대 값을 가진 레코드를 조회한다.
2. GROUP BY FOOD_TYPE : FOOD_TYPE을 기준으로 그루핑한다.
3. ORDER BY FOOD_TYPE DESC : FOOD_TYPE을 기준으로 내림차순 정렬한다.

<br>
<br>

# 3. 다른 풀이

```sql
SELECT FOOD_TYPE, REST_ID, REST_NAME, FAVORITES
FROM REST_INFO
WHERE FAVORITES IN (
    SELECT MAX(FAVORITES)
    FROM REST_INFO
    GROUP BY FOOD_TYPE
)
GROUP BY FOOD_TYPE
ORDER BY FOOD_TYPE DESC
```

1. SELECT FOOD_TYPE, REST_ID, REST_NAME, FAVORITES FROM REST_INFO : REST_INFO 테이블의 FOOD_TYPE, REST_ID, REST_NAME, FAVORITES 컬럼을 조회한다.
2. WHERE FAVORITES IN (서브쿼리) : 서브쿼리로 음식 종류별로 가장 별점이 높은 별점을 찾아낸 후 WHERE절의 IN을 활용하여 FAVORITES 컬럼의 일치하는 레코드를 조회한다.
3. GROUP BY FOOD_TYPE : FOOD_TYPE을 기준으로 그루핑한다.
4. ORDER BY FOOD_TYPE DESC : FOOD_TYPE을 기준으로 내림차순 정렬한다.

<br>
<br>

# 4. 후기

GROUP BY와 WHERE절의 IN에 대해 공부할 수 있었다. 나의 풀이의 경우 실행해보면 즐겨찾기가 가장 많은 식당 정보를 출력하기는 하지만 정답은 아니었다. 왜냐하면 REST_NAME과 FAVORITES이 매칭되지 않기 때문이다. 이유는 GROUP BY를 통해 음식 종류별로 데이터를 묶은 후 가장 맨 첫 번째 데이터를 가져오기 때문에 매칭되지 않는 문제점이 발생하기 때문이다. 이번 풀이는 실패했다. 다른 풀이의 경우 이러한 문제를 서브쿼리를 활용하여 구하였다.

- GROUP BY : 동일한 값을 가진 컬럼을 그루핑할 때 사용한다. 대부분 집계함수와 함께 사용된다.
- WHERE절의 IN : 주어진 값을 가진 레코드를 찾을 때 사용한다.
- 서브쿼리 : 하나의 쿼리에서 SELECT 문 안에 또 다른 SELECT 문이 있을 때, 안에 포함된 SELECT 문이 서브쿼리

<br>
