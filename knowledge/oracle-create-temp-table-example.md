# 오라클 Temp 테이블 생성 예제

## 세션 임시 테이블 (ON COMMIT PRESERVE ROWS)
세션 단위로 데이터가 관리되며 다른 세션의 데이터를 볼 수 없다. 세션이 종료될 경우 데이터는 자동적으로 사라진다. (MS-SQL의 TEMP 테이블과 유사)

``` sql
CREATE GLOBAL TEMPORARY TABLE TMP_테이블명
(
  ...
) ON COMMIT PRESERVE ROWS;
```

## 트랜잭션 임시 테이블 (ON COMMIT DELETE ROWS)
트랜잭션 단위로 데이터가 관리되며, 커밋을 하면 데이터가 사라진다. 현재 세션에서 커밋이 발생하더라도 다른 세션에서 사용하는 데이터는 사라지지 않는다.

``` sql
CREATE GLOBAL TEMPORARY TABLE TMP_테이블명
(
  ...
) ON COMMIT DELETE ROWS;
```