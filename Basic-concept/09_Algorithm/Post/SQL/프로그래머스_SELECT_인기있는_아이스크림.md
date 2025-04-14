# [Algorithm-SQL] 프로그래머스 - SELECT - 인기있는 아이스크림

2025년 04월 14일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/133024

<br>
<br>

# 2. 나의 풀이

```sql
-- 코드를 입력하세요
SELECT FLAVOR FROM FIRST_HALF
ORDER BY TOTAL_ORDER DESC, SHIPMENT_ID
```

1. FIRST_HALF 테이블의 FLAVOR 컬럼을 조회한다.
2. 결과는 총 주문수를 기준으로 내림차순 정렬하고, 총 주문수가 같다면 아이디를 기준으로 오름차순 정렬해야하기 때문에 ORDER BY에 순차적으로 해당 정렬 조건을 추가한다.

<br>
<br>

# 3. 후기

- 정렬만 사용하는 쉬운 문제였다. ORDER BY 사용 시 정렬을 여러번 할 수 있다는 점만 알면 쉽게 해결할 수 있는 문제였다.

<br>
