# Basic SQL

### table 생성

```sql
CREATE TABLE supplychain (
	ID_BB_COMPANY INT4,
    LONG_COMP_NAME VARCHAR(100),
    ...
    STANDRD_RELTNSHP_VALUE FLOAT8
);
```

**CREATE TABLE** + table_name: table 생성

괄호 안에 아래와 같이 column name과 해당 column의 data type

`col_name` [`data type`] => col_name



### SELECT ~ FROM

```sql
SELECT select_cols
FROM table_name
WHERE condition;
```

`SELECT` : 조회하고자 하는 column들

`FROM`: 조회하려는 table 이름

`WHERE`: 조회 조건



### ORDER BY

```sql
SELECT select_cols
FROM table_name
WHERE condition;
ORDER BY col1 DESC
LIMIT 10;
```

`OREDER BY`: 정렬 기준으로 삼을 column name + `DESC / ASC`: 정렬 방향 (default: `ASC`)

`LIMIT`: 출력 제한, 뒤에 입력한 숫자만큼 row를 출력



### JOIN

```sql
SELECT select_cols
FROM table_name original
JOIN another_table_name coming
ON original.column1 = coming.column1
```

> `join?` => 두 개 이상의 테이블에 대해서 결합하는 작업

`JOIN`: join할 table (INNER JOIN)

`ON` join 조건



### GROUP BY

```sql
SELECT column1, SUM(column2)
FROM table_name
GROUP_BY column1
ORDER_By column1;
```

`GROUP BY`: 

`aggregate_function`: 







