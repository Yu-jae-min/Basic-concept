# [Algorithm-SQL] 프로그래머스 - SUM, MAX, MIN - 최댓값 구하기

2023년 12월 28일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/59415

<br>
<br>

# 2. 나의 풀이

## 2-1. 나의 풀이(1)

```sql
SELECT DATETIME as 시간
FROM ANIMAL_INS
ORDER BY DATETIME DESC
LIMIT 1
```

1. SELECT DATETIME as 시간 FROM ANIMAL_INS : ANIMAL_INS 테이블의 DATETIME 컬럼을 조회한다. 이 때 결과 컬럼명을 시간으로 치환한다.
2. ORDER BY `DATETIME` DESC : `DATETIME` 컬럼 값을 기준으로 내림차순 정렬한다.
3. LIMIIT 1 : 가장 최상위에 있는 레코드를 조회한다.

<br>

### 2-2. 나의 풀이(2)

```sql
SELECT MAX(DATETIME) as 시간 FROM ANIMAL_INS
```

s

1. `MAX` 함수를 사용하여 최댓값을 구할 수 있다. 위 코드에서 ANIMAL_INS 테이블 안에 있는 DATETIME 컬럼을 MAX 함수의 파라미터로 전달하여 즉시 최댓값을 조회할 수 있다.
2. as를 사용하여 결과 값 컬럼명을 변경하여 레코드를 조회한다.

<br>
<br>

# 3. 후기

첫 번째 풀이의 경우 이 전에 문제들과 마찬가지로 풀이해보았다. 기준이 되는 컬럼을 기준으로 내림차순 정렬을 한 뒤 LIMIT를 통해 가장 최근에 들어온 동물을 구하였다. 두 번째 풀이의 경우 프로그래머스 알고리즘에서 유도하는 것처럼 MAX 함수를 사용하였다. 두 풀이의 비교해보면 `MAX` 함수를 사용하는 경우가 훨씬 간결한 것을 알 수 있었다. 최댓값을 구할 때 유용하게 사용할 수 있을 것 같다.

<br>
