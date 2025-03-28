# [Algorithm-SQL] 프로그래머스 - SELECT - 강원도에 위치한 생산공장 목록 출력하기

2025년 03월 28일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/131112

<br>
<br>

# 2. 나의 풀이

```sql
SELECT FACTORY_ID, FACTORY_NAME, ADDRESS FROM FOOD_FACTORY
WHERE ADDRESS LIKE '강원도%'
ORDER BY FACTORY_ID
```

1. FOOD_FACTORY 테이블의 FACTORY_ID, FACTORY_NAME, ADDRESS 컬럼을 조회한다.
2. 특정 지역에 위치한 공장을 찾기 위해 WHERE절을 사용하고 이 때 강원도에 위치하는 공장을 찾기 위해 LINK 연산자를 활용하여 데이터를 찾는다.
3. FACTORY_ID 기준으로 오름차순 정렬을 위해 ORDER BY로 정렬한다.

<br>
<br>

# 3. 후기

- 특정 문자열이 포함된 데이터를 찾을 때는 `LINK`를 사용할 수 있다.

  - LIKE : 특정 문자를 포함하는 데이터를 출력
  - NOT LIKE : 특정 문자를 포함하지 않는 데이터를 출력
  - 컬럼 LIKE '문자%' : 특정 문자로 시작하는 데이터 확인
  - 컬럼 LIKE '%문자' : 특정 문자로 종료하는 데이터 확인
  - 컬럼 LIKE '%문자%' : 문자 시작 ~ 종료까지 특정 문자 포함 여부 확인

<br>
