# [Algorithm-SQL] 프로그래머스 - SELECT - 여러 기준으로 정렬하기

2023년 12월 21일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/59404

<br>
<br>

# 2. 나의 풀이

```sql
SELECT ANIMAL_ID, NAME, DATETIME
FROM ANIMAL_INS
ORDER BY NAME ASC, DATETIME DESC
```

1. FROM : ANIMAL_INS 테이블을 조회한다.
2. SELECT : ANIMAL_ID, NAME, DATETIME 컬럼을 조회한다.
3. ORDER BY : 우선 이름을 오름차순 순으로 정렬한 뒤 날짜를 기준으로 다시 한번 내림차순으로 정렬한다. 즉 이름으로 정렬된 데이터 중 이름이 같은 경우 날짜를 기준으로 내림차순 정렬하는 것이다.

<br>
<br>

# 3. 후기

해당 문제를 풀며 여러 기준으로 정렬하는 방법에 대해 습득할 수 있었다. 조회하는 데이터의 정렬 시 참고하는 컬럼이 많은 경우 유용할 것 같다.

<br>
