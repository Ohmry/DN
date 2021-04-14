# 오라클 WHILE 사용 예제
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