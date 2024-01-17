# [Algorithm-SQL] 프로그래머스 - GROUB BY - 년, 월, 성별 별 상품 구매 회원 수 구하기

2024년 01월 17일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/131532

<br>
<br>

# 2. 나의 풀이

```sql
SELECT YEAR(ONLINE_SALE.SALES_DATE) as YEAR, MONTH(ONLINE_SALE.SALES_DATE) as MONTH,
USER_INFO.GENDER as GENDER, COUNT(DISTINCT ONLINE_SALE.USER_ID) as USERS
FROM ONLINE_SALE
JOIN USER_INFO ON ONLINE_SALE.USER_ID = USER_INFO.USER_ID
WHERE GENDER IS NOT NULL
GROUP BY YEAR, MONTH, GENDER
ORDER BY YEAR, MONTH, GENDER
```

1. 1~2행에서 필요한 테이블의 컬럼을 조회하는데 이 때 두 테이블의 컬럼을 조회하기 때문에 3행에서 JOIN을 통해 두 테이블을 묶어주었다.
2. 1~2행에서 필요한 테이블의 컬럼을 조회하는데 년, 월, 성별별로 나누어 조회해야하기 때문에 날짜 관련 함수를 사용하였다. 날짜 관련 함수 YEAR, MONTH 등을 통해 0000-00-00 형식의 데이터에서 년과 월을 추출해주었다. 또한 년, 월, 성별별로 구매한 회원을 추출해내야하기 때문에 동일한 유저의 중복을 제거하기 위해서 DISTINCT 절을 활용하여 중복 데이터 제거 후 COUNT를 통해 년, 월, 성별별로 구매한 회원의 수를 집계하였다.
3. 4행에서 성별을 가지고 있지 않은 행을 제외시켰다.
4. 5행에서 년, 월, 성별별로 그루핑을 하였다. 즉 년, 월, 성별이 모두 같은 데이터를 집계하기 위해서 그루핑한 것이다. 만약 그루핑 하지 않는다면 년, 월은 마지막 행의 데이터의 값을 가지게 되고 하나의 행으로 표현될 것이다.

   1. 그루핑 O

      <img width="967" alt="Algorithm_SQL_프로그래머스_GROUB_BY_년_월_성별_별_상품_구매_회원_수_구하기_01" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/58a88861-f1ed-4699-b517-cdaf6c75e416">

   2. 그루핑 X

      <img width="979" alt="Algorithm_SQL_프로그래머스_GROUB_BY_년_월_성별_별_상품_구매_회원_수_구하기_02" src="https://github.com/Yu-jae-min/Basic-concept/assets/85284246/0c21fb04-d386-4266-b13a-d850ff8cefe2">

5. 6행에서 ORDER BY를 통해 년, 월, 성별 순으로 오름차순 정렬해주었다.

<br>
<br>

# 3. 후기

- 날짜 관련 함수, JOIN, DISTINCT에 대해서 배울 수 있었다.

- `날짜 관련 함수`

  - YAER : 년을 추출한다.

  - MONTH : 월을 추출한다.

- `JOIN`

  - 조인은 두 개의 테이블을 서로 묶어서 하나의 결과를 만들어 내는 것을 말한다.

  - INNER JOIN(내부 조인) : 두 테이블을 조인할 때, 두 테이블에 모두 지정한 열의 데이터가 있어야 한다.

  - OUTER JOIN(외부 조인) : 두 테이블을 조인할 때, 1개의 테이블에만 데이터가 있어도 결과가 나온다.

  - CROSS JOIN(상호 조인) : 한쪽 테이블의 모든 행과 다른 쪽 테이블의 모든 행을 조인하는 기능이다.

  - SELF JOIN(자체 조인) : 자신이 자신과 조인한다는 의미로, 1개의 테이블을 사용한다.

- `DISTINCT`

  - 중복 데이터를 제거한다.

<br>
