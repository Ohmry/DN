# 오라클DB 관련 개발노트
  - [임시테이블 생성 예제](#임시테이블-생성-예제)
  - [커서(CURSOR) 사용 예제](#커서cursor-사용-예제)
  - [반복문(WHILE) 사용 예제](#반복문while-사용-예제)
  - [시퀀스 제어 예제](#시퀀스-제어-예제)
  - [PIVOT 예제](#pivot-예제)
  - [UNPIVOT 예제](#unpivot-예제)
  
## 임시테이블 생성 예제
### 세션 임시 테이블 (ON COMMIT PRESERVE ROWS)
세션 단위로 데이터가 관리되며 다른 세션의 데이터를 볼 수 없다. 세션이 종료될 경우 데이터는 자동적으로 사라진다. (MS-SQL의 TEMP 테이블과 유사)

``` sql
CREATE GLOBAL TEMPORARY TABLE TMP_테이블명
(
  ...
) ON COMMIT PRESERVE ROWS;
```

### 트랜잭션 임시 테이블 (ON COMMIT DELETE ROWS)
트랜잭션 단위로 데이터가 관리되며, 커밋을 하면 데이터가 사라진다. 현재 세션에서 커밋이 발생하더라도 다른 세션에서 사용하는 데이터는 사라지지 않는다.

``` sql
CREATE GLOBAL TEMPORARY TABLE TMP_테이블명
(
  ...
) ON COMMIT DELETE ROWS;
```

## 커서(CURSOR) 사용 예제
``` sql
DECLARE
  I_BRCH_NO   VARCHAR2(4);
  CURSOR I_CUR IS
  SELECT  BRCH_NO
  FROM    ${TABLE};
BEGIN
  OPEN I_CUR;
  
  LOOP
  FETCH I_CUR INTO I_BRCH_NO;
  EXIT WHEN I_CUR %NOTFOUND;
    -- 루프 처리구문
    DBMS_OUTPUT.PUT_LINE(I_BRCH_NO);
  END LOOP;

  CLOSE I_CUR;  
END;  
```

## 반복문(WHILE) 사용 예제
``` sql
DECLARE
  I_NUMBER    NUMBER;
BEGIN

  I_NUMBER := 1;

  -- 1부터 10까지 루프
  WHILE I_NUMBER <= 10  
  LOOP
    DBMS_OUTPUT.PUT_LINE(I_NUMBER);
    I_NUMBER := I_NUMBER + 1;
  END LOOP;

END;
```

## 시퀀스 제어 예제
``` sql
-- 시퀀스의 LastValue 값 확인
SELECT * FROM USER_SEQUENCES WHERE SEQUENCE_NAME = ${시퀀스명};

-- 시퀀스 증가량 조정
ALTER SEQUENCE ${시퀀스명} INCREMENT BY ${증가량};

-- 시퀀스 증가
SELECT ${시퀀스명}.NEXTVAL FROM DUAL;

-- 시퀀스 증가량을 원래대로 돌려놓는다.
ALTER SEQUENCE ${시퀀스명} INCREMENT BY 1;
```

## PIVOT 예제
``` sql
WITH SD AS (
  SELECT 'A' AS TY, 'JAN' AS MM, 10 AS CNT FROM DUAL UNION ALL
  SELECT 'A' AS TY, 'FEB' AS MM, 5 AS CNT FROM DUAL UNION ALL
  SELECT 'B' AS TY, 'JAN' AS MM, 10 AS CNT FROM DUAL UNION ALL
  SELECT 'C' AS TY, 'MAR' AS MM, 8 AS CNT FROM DUAL
)
SELECT  *
FROM  SD
PVIOT (
    SUM(CNT)
    FOR MM IN ('JAN', 'FEB', 'MAR')
)
```

## UNPIVOT 예제
``` sql
WITH SD AS (
  SELECT  'A' AS TY, 10 AS JAN, 5 AS FEB, 0 AS MAR FROM DUAL UNION ALL
  SELECT  'B' AS TY, 10 AS JAN, 0 AS FEB, 0 AS MAR FROM DUAL UNION ALL
  SELECT  'C' AS TY, 0 AS JAN, 0 AS FEB, 8 AS MAR FROM DUAL
)
SELECT  *
FROM  SD
UNPVIOT (
    CNT
    FOR 'MM' IN ('JAN', 'FEB', 'MAR')
)
```