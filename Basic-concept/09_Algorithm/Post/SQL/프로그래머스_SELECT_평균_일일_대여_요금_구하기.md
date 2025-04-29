# [Algorithm-SQL] 프로그래머스 - SELECT - 평균 일일 대여 요금 구하기

2025년 04월 29일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/151136

<br>
<br>

# 2. 나의 풀이

```sql
-- 코드를 입력하세요
SELECT ROUND((SUM(DAILY_FEE) / COUNT(*)), 0) as AVERAGE_FEE
FROM CAR_RENTAL_COMPANY_CAR
WHERE CAR_TYPE LIKE '%SUV%'
```

1. CAR_RENTAL_COMPANY_CAR 테이블의을 조회한다. 이 때 SUV의 평균을 구해야하므로 `SUM`을 통해 일일 대여 요금을 모두 더하고 `COUNT`를 통해 컬럼의 개수를 구한 뒤 해당 값으로 나눈다. 이 때 결과 값은 소수점 첫 번째 자리에서 반올림 해야 하므로 `ROUND` 를 사용하며 두 번째 인자로 0을 지정한다. 그리고 최종 값은 컬럼명이 AVERAGE_FEE이므로 별칭을 지정한다.
2. WHERE절로 조건을 추가한다. 조건은 CAR_TYPE가 SUV인 경우이므로 LIKE을 활용하여 문자가 SUV인 경우로 필터한다.

<br>
<br>

# 3. 후기

- 소수점 반올림, 올림 처리는 `ROUND`, `CEILING` 를 활용하여 처리할 수 있다.
- `ROUND` : 소수점 반올림
  - ROUND('수치값', '반올림 자릿수')
  - 반올림 자릿수의 경우 index이다. 첫 번째 자릿수의 경우 0부터 시작한다.
  - 음수도 입력 가능하다. 음수 입력하여 정수를 반올림 처리할 수 있다. 예를 들어 ROUND(56789, -1)인 경우 56790이 된다.
- `CEILING` : 소수점 올림
  - CEILING('수치값')
  - 소수점이 있는 경우 무조건 올림 처리한다.

<br>
