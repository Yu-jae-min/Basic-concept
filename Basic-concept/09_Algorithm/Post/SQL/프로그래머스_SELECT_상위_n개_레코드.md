# [Algorithm-SQL] 프로그래머스 - SELECT - 상위 n개 레코드

2023년 12월 22일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/59405

<br>
<br>

# 2. 나의 풀이

```sql
SELECT NAME
FROM ANIMAL_INS
ORDER BY DATETIME
LIMIT 1
```

1. FROM : ANIMAL_INS 테이블을 조회한다.
2. SELECT : NAME 컬럼을 조회한다.
3. ORDER BY : DATETIME 컬럼 데이터를 기준으로 오름차순 정렬한다. ORDER BY의 기본 값은 오름차순(ASC)이다.
4. LIMIT : LIMIT는 결괏값 레코드 개수를 제한할 수 있다. LIMIT 개수 혹은 LIMIT offset, 개수과 같이 지정할 수 있다. 위 풀이에서는 개수만 지정하였으므로 최상위 데이터가 조회된다.

<br>
<br>

# 3. 후기

해당 문제를 풀며 특정 레코드 갯수를 제한하여 조회하는 방법을 알 수 있었다. 예를 들어 특정 레코드의 값으로 유저들의 순위를 판별하거나 할 때 사용할 수 있을 것 같다.

<br>
