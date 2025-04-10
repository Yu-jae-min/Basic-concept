# [Algorithm-SQL] 프로그래머스 - SELECT - 12세 이하인 여자 환자 목록 출력하기

2025년 04월 10일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/132201

<br>
<br>

# 2. 나의 풀이

```sql
-- 코드를 입력하세요
SELECT PT_NAME, PT_NO, GEND_CD,AGE,
IF(TLNO is NULL, 'NONE', TLNO) as TLNO
FROM PATIENT
WHERE AGE <= 12 and GEND_CD = 'W'
ORDER BY AGE DESC, PT_NAME
```

1. PATIENT 테이블의 PT_NAME, PT_NO, GEND_CD, TLNO 컬럼을 조회한다.
2. 컬럼 조회 시 TLNO 컬럼의 경우 행의 데이터가 null인 경우 ‘NONE’으로 치환해야 하기 때문에 IF절을 활용하여 치환한다.
3. 12세 이하인 여자 환자 목록을 출력해야하기 때문에 WHERE절을 활용하여 나이와 성별 조건을 추가한다.
4. 결과는 나이를 기준으로 내림차순 정렬하고, 나이 같다면 환자이름을 기준으로 오름차순 정렬해야하기 때문에 ORDER BY에 순차적으로 해당 정렬 조건을 추가한다.

<br>
<br>

# 3. 후기

- `WHERE`절 사용 시 조건은 and를 통해 여러 개를 생성할 수 있다.
- `ORDER BY`를 사용하여 행 정렬 시 여러 개의 정렬 조건을 이어서 사용할 수 있다. 위와 같은 경우 AGE로 우선 내림차순을 수행하고, AGE가 같다면 다음 정렬 조건인 PT_NAME를 통해 오름차순 정렬하는 것이다.

<br>
