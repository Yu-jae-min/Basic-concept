# [Algorithm-SQL] 프로그래머스 - SELECT - 과일로 만든 아이스크림 고르기

2025년 04월 15일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/133025

<br>
<br>

# 2. 나의 풀이

```sql
-- 코드를 입력하세요
SELECT f.FLAVOR
FROM FIRST_HALF AS f
JOIN ICECREAM_INFO AS i ON f.FLAVOR = i.FLAVOR
WHERE f.TOTAL_ORDER > 3000
AND i.INGREDIENT_TYPE = 'fruit_based'
ORDER BY f.TOTAL_ORDER DESC;
```

1. FIRST_HALF 테이블, ICECREAM_INFO 테이블을 조회한다. 이 때 테이블의 이름이 길기 때문에 공백 혹은 `AS`를 활용하여 별칭을 지정하고 FIRST_HALF의 FLAVOR는 기본키, ICECREAM_INFO의 FLAVOR는 외래키이므로 해당 키와 `ON`을 활용하여 테이블을 연결한다. 그리고 최종 결과 컬럼은 FLAVOR이므로 `.(도트 연산자)`을 활용하여 FIRST_HALF 테이블에 FLAVOR을 조회한다.
2. 조건은 FIRST_HALF 테이블에 TOTAL_ORDER(총 주문량)이 3000 초과, ICECREAM_INFO 테이블에 INGREDIENT_TYPE이 과일인 경우로 필터해야하기 때문에 `WHERE`절과 `AND`를 활용한다.
3. 최종적으로 FIRST_HALF 테이블에 TOTAL_ORDER(총 주문량)을 기준으로 내림차순한다.

<br>
<br>

# 3. 후기

- 별칭 지정 `AS`와 `공백`

  - 별칭 지정을 위해 `AS`와 `공백` 모두 활용할 수 있다.

  - 아래 결과물은 같다.
    ```sql
    SELECT f.FLAVOR FROM FIRST_HALF AS f // AS를 통한 별칭 지정
    SELECT f.FLAVOR FROM FIRST_HALF f // 공백을 통한 별칭 지정
    ```

- 테이블 연결을 위한 `JOIN`과 `ON`

  - SELECT절을 통해 테이블 조회 시 `JOIN`을 통해 테이블을 연결할 수 있다. 다만 ON을 사용하지 않는 경우 카티션 곱이 발생하므로 ON을 사용하여 키를 연결해주어야한다.
  - `ON` 조건절은 테이블 연결을 위해 사용된다. 보통 외래키, 기준키를 사용하여 연결한다.

<br>
