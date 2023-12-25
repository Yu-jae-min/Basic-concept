# [Algorithm-SQL] 프로그래머스 - SELECT - 조건에 맞는 회원수 구하기

2023년 12월 25일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/131535

<br>
<br>

# 2. 나의 풀이

```sql
SELECT COUNT(*)
FROM USER_INFO
WHERE AGE >= 20 AND AGE <= 29 AND YEAR(JOINED) = 2021
```

1. FROM : USER_INFO 테이블을 조회한다.
2. SELECT : 모든 컬럼을 조회한다. 이 때 몇 명인지 조회하는 것이기 때문에 COUNT를 활용한다.
3. WHERE : 조건을 추가한다. 이 때 20세 이상, 29세 이하, 가입한 연도가 2021년이라는 조건을 추가하는데 AND로 이어준다. 가입연도의 경우 YEAR을 통해 연도를 추출하여 조건에 활용한다.

<br>
<br>

# 3. 후기

- COUNT : 결과 값의 개수를 조회
- `*` : 모든 컬럼을 조회
- AND : 조건문을 이어 작성할 수 있다.
- YEAR : 연도 추출

<br>
