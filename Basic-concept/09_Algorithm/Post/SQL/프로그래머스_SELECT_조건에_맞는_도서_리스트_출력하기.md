# [Algorithm-SQL] 프로그래머스 - SELECT - 조건에 맞는 도서 리스트 출력하기

2025년 04월 18일

<br>

# 1. 문제

- https://school.programmers.co.kr/learn/courses/30/lessons/144853

<br>
<br>

# 2. 나의 풀이

```sql
-- 코드를 입력하세요
SELECT BOOK_ID, DATE_FORMAT(PUBLISHED_DATE, '%Y-%m-%d') AS PUBLISHED_DATE
FROM BOOK
WHERE CATEGORY = '인문' AND PUBLISHED_DATE LIKE '2021%'
ORDER BY PUBLISHED_DATE
```

1. PUBLISHED_DATE 테이블의 BOOK_ID, PUBLISHED_DATE 컬럼을 조회하는데, DATE_FORMAT를 활용하여 PUBLISHED_DATE의 날짜 포맷을 변경한 뒤 별칭을 PUBLISHED_DATE로 재지정하여 조회한다.
2. WHERE절로 조건을 추가한다. 조건은 CATEGORY가 인문인 경우, PUBLISHED_DATE가 2021년인 경우이므로 LIKE을 활용하여 2021로 시작되는 문자인 경우로 필터한다.
3. PUBLISHED_DATE 기준으로 오름차순 정렬한다.

<br>
<br>

# 3. 후기

- `DATE_FORMAT` 을 통해 날짜 포맷을 변경한다.
- 특정 문자열이 포함된 데이터를 찾을 때는 `LIKE`을 사용할 수 있다.
  - LIKE : 특정 문자를 포함하는 데이터를 출력
  - NOT LIKE : 특정 문자를 포함하지 않는 데이터를 출력
  - 컬럼 LIKE '문자%' : 특정 문자로 시작하는 데이터 확인
  - 컬럼 LIKE '%문자' : 특정 문자로 종료하는 데이터 확인
  - 컬럼 LIKE '%문자%' : 문자 시작 ~ 종료까지 특정 문자 포함 여부 확인

<br>
