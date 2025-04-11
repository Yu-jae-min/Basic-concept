# [Algorithm-SQL] 프로그래머스 - SELECT - 흉부외과 또는 일반외과 의사 목록 출력하기

2025년 04월 11일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/132203

<br>
<br>

# 2. 나의 풀이

```sql
-- 코드를 입력하세요
SELECT DR_NAME, DR_ID, MCDP_CD, DATE_FORMAT(HIRE_YMD, '%Y-%m-%d')
FROM DOCTOR
WHERE MCDP_CD = 'CS' OR MCDP_CD = 'GS'
ORDER BY HIRE_YMD DESC, DR_NAME
```

1. DOCTOR 테이블의 DR_NAME, DR_ID, MCDP_CD, DATE_FORMAT 컬럼을 조회한다.
2. 컬럼 조회 시 HIRE_YMD 컬럼의 경우 행의 날짜 포맷을 치환해야하므로 DATE_FORMAT을 활용한다.
3. 진료과(MCDP_CD)가 흉부외과(CS)이거나 일반외과(GS)인 의사만 조회해야하므로 WHERE절과 OR을 활용하여 두 조건 중 하나라도 참인 경우의 데이터를 조회한다.
4. 결과는 고용일자를 기준으로 내림차순 정렬하고, 고용일자가 같다면 이름을 기준으로 오름차순 정렬해야하기 때문에 ORDER BY에 순차적으로 해당 정렬 조건을 추가한다.

<br>
<br>

# 3. 후기

- `WHERE`절 사용 시 조건은 `or`을 통해 ~이거나의 조건을 생성할 수 있다.
- 날짜 포맷 변환 시 `DATE_FORMAT`을 활용할 수 있다.
  - DATE_FORMAT(date, format)
    - `date`: 날짜 또는 시간 값 (예: `created_at`, `'2024-04-10 15:30:00'`)
    - `format`: 변환할 형식을 지정하는 문자열

<br>
