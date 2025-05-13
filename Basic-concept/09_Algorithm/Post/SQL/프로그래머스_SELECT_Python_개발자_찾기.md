# [Algorithm-SQL] 프로그래머스 - SELECT - Python 개발자 찾기

2025년 05월 14일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/276013

<br>
<br>

# 2. 나의 풀이

```sql
-- 코드를 작성해주세요
SELECT ID, EMAIL, FIRST_NAME, LAST_NAME FROM DEVELOPER_INFOS
WHERE SKILL_1 = 'Python' OR SKILL_2 = 'Python' OR SKILL_3 = 'Python'
ORDER BY ID
```

1. DEVELOPER_INFOS 테이블을 조회한다. 이 때 ID, EMAIL, FIRST_NAME, LAST_NAME 컬럼을 조회한다.
2. 스킬이 파이썬인 개발자를 찾기 위해 `WHERE` 조건문을 활용하는데, 스킬이 1-3까지 있으므로 `OR`을 통해 여러 조건으로 스킬이 Python인 개발자를 찾는다.
3. ID를 기준으로 오름차순 정렬한다.

<br>
<br>

# 3. 후기

- `OR` : 조건문 사용 시 ‘또는’ 여러 조건을 달 수 있다.

<br>
