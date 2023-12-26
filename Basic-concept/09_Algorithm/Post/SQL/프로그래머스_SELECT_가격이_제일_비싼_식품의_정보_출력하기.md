# [Algorithm-SQL] 프로그래머스 - SELECT - 가격이 제일 비싼 식품의 정보 출력하기

2023년 12월 26일

<br>
<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/131115

<br>
<br>

# 2. 나의 풀이

```sql
SELECT *
FROM FOOD_PRODUCT
ORDER BY PRICE DESC
LIMIT 1
```

1. SELECT `*` FROM `FOOD_PRODUCT` : FOOD_PRODUCT 테이블의 전체 레코드를 조회한다.
2. ORDER BY `PRICE` DESC : `PRICE` 컬럼 값을 기준으로 내림차순 정렬한다.
3. LIMIIT 1 : 가장 최상위에 있는 레코드를 조회한다.

<br>
<br>

# 3. 후기

이전에 풀었던 문제와 유사하다. 가장 비싼 가격의 레코드를 조회하기 위해 정렬한 후 최상위 레코드를 추출하였다.

<br>
