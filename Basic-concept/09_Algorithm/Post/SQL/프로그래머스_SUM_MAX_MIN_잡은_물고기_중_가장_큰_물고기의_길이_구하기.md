# [Algorithm-SQL] 프로그래머스 - SELECT - 잡은 물고기 중 가장 큰 물고기의 길이 구하기

2025년 05월 01일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/298515

<br>
<br>

# 2. 나의 풀이

```sql
-- 코드를 작성해주세요
SELECT CONCAT(MAX(LENGTH), 'cm') AS MAX_LENGTH
FROM FISH_INFO
```

1. FISH_INFO 테이블을 조회한다. 가장 큰 길이의 물고기를 구하기 위해 `MAX`를 활용한다. 그 후 단위인 cm를 이어붙이기 위해 `CONCAT`을 활용한다. 최종적으로 컬럼명은 MAX_LENGTH가 되므로 별칭을 지정한다.

<br>
<br>

# 3. 후기

- `MAX` : 최대 값을 가진 행을 반환한다.
- `CONCAT` : 문자를 이어붙일 때 활용한다.
  - CONCAT(str1, str2, ..., strN)

<br>
