# [Algorithm-SQL] 프로그래머스 - SUM, MAX, MIN - 동물 수 구하기

2023년 12월 31일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/59406

<br>
<br>

# 2. 나의 풀이

```sql

SELECT COUNT(*) FROM ANIMAL_INS
```

1. SELECT `COUNT`(\*) FROM ANIMAL_INS : ANIMAL_INS 테이블의 모든 컬럼의 레코드를 조회하는데 COUNT 함수를 활용하여 레코드의 총합 갯수를 구하였다.

<br>
<br>

# 3. 후기

프로그래머스에서 SUM, MAX, MIN 카테고리에 들어있는 문제라서 SUM 함수를 활용하여 푸는 문제인 줄 알았으나 레코드 갯수를 구해야하기에 COUNT 함수를 활용하였다. 문제를 해결한 후 SUM 함수를 사용해보지 않아 COUNT 함수와 SUM 함수를 비교해보니 COUNT 함수는 레코드의 개수를 구할 수 있고 SUM 함수는 레코드 내부 데이터의 합산을 구할 수 있는 함수였다. 두 함수의 차이점을 잘 기억해야겠다.

<br>
