# [Algorithm-SQL] 프로그래머스 - SUM, MAX, MIN - 가장 비싼 상품 구하기

2025년 04월 09일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/131697

<br>
<br>

# 2. 나의 풀이

```sql
SELECT MAX(PRICE) AS MAX_PRICE FROM PRODUCT
```

1. PRODUCT 테이블의 PRICE 컬럼을 조회한다. 이 때 MAX를 활용하여 해당 컬럼의 최대 값을 가진 행을 조회한다. 최종 결과는 MAX_PRICE라는 이름의 컬럼으로 반환해야하기 때문에 AS를 활용하여 컬럼에 별칭을 지정한다.

<br>
<br>

# 3. 후기

- `MAX` : 해당 컬럼의 최대 값을 가진 행을 조회한다.

<br>
