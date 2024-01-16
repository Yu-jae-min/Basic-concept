# [Algorithm-SQL] 프로그래머스 - GROUB BY - 동명 동물 수 찾기

2024년 01월 16일

<br>
<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/59041

<br>
<br>

# 2. 나의 풀이

```sql
SELECT NAME, COUNT(NAME) AS 'COUNT' FROM ANIMAL_INS
WHERE NAME IS NOT NULL
GROUP BY NAME
HAVING COUNT(NAME) > 1
ORDER BY NAME
```

1. 1행에서 ANIMAL_INS 테이블의 NAME을 조회하고 NAME을 카운트한다. 이 때 AS 키워드를 통해 원하는 컬럼명으로 바꿔서 데이터를 나타내도록 한다.
2. 2행에서 이름이 없는 동물을 제외하기 위해 WHERE 조건문과 IS NOT NULL을 함께 사용하여 이름이 없는 동물을 제외시킨다.
3. 3행에서 GROUP BY를 통해 NAME 컬럼의 데이터를 그루핑한다.
4. 4행에서 GROUP BY를 통해 그루핑한 집합에 특정 조건에 부합하는 데이터를 조회하기 위해 조건을 걸어준다. 집합에 특정 조건을 걸어주기 위해서는 HAVING 절을 사용해야하며 HAVING 절을 사용하여 카운트 된 이름이 1보다 큰 경우, 즉 2번 이상 쓰인 경우를 조건으로 그루핑 된 집합의 특정 데이터를 조회하였다.
5. 5행에서 ORDER BY를 통해 오름차순 정렬해준다.

<br>
<br>

# 3. 후기

- `HAVING` 절이라는 새로운 절을 배울 수 있었다.
- `HAVING` 절
  - HAVING 절은 GROUP BY 절의 기준 항목이나 소그룹의 집계 함수를 이용한 조건을 표시할 수 있다.
  - GROUP BY 절에 의한 소그룹별로 만들어진 집계 데이터 중, HAVING 절에서 제한 조건을 두어 조건을 만족하는 내용만 출력한다.
  - HAVING 절은 일반적으로 GROUP BY 절 뒤에 위치한다.

<br>
