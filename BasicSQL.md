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

> JOIN 종류
>
> - `inner join`:  기준 테이블과 조인 테이블 모두 데이터가 존재해야 조회 가능
> - `outer join`: 기준 테이블에만 데이터가 존재해도 조회 가능 
>   - **left** / **right** / **full** => join 기준 기준 테이블/ 참조 테이블/ 모두
> - `self join`: 동일한 테이블 사이의 join
>   - ex) 지하철 정보 테이블에서 다음 역에 대한 column이 있는 경우, 다음 역에 대한 정보는 바로 조회 가능 하지만 2 정거장 이후에 대한 정보는 구할 수 없다. 이러한 경우 self join을 사용하여 원하는 정보를 조회할 수 있다.



### GROUP BY

```sql
SELECT column1, SUM(column2)
FROM table_name
GROUP_BY column1
ORDER_By column1;
```

`GROUP BY`: 해당 column에 속하는 row가 많은 경우, aggregate_func을 사용하여 해당 정보들을 집계 해줌

`aggregate_function`: 변수로 입력한 값들의 집합에 대한 계산을 수행하고 단일 값을 반환

> `AVG`, `COUNT`, `MAX`, `MIN`, `STDEV`,  `SUM`, `VAR` 등이 있음



### NESTED Query

```sql
SELECT r.a, r.b, l.c
FROM (
	SELECT c, d, e
	FROM left
	WHERE c is not null and f = 'STH'
) As l
JOIN right r ON l.d = r.d
and l.e = r.e
ORDER BY l.c DESC;
```

`nested Query`: query문을 이용하여 만든 테이블을 기반으로 다시 Query문을 작성. 말 그대로 Query문이 `nested`되어있는 형태

**Query문 해석**

"[`left 테이블(FROM left)`에서 

`c 값이 null이 아니고 f의 값이 'STH'(WHERE c is not null and f = 'STH')`인 row들의

 `c, d, e(SELECT c, d, e)` column을 가져온 테이블(as l)]

=> 여기까지 nested

을 `right 테이블(JOIN right)`과 

`두 테이블의 d, e column이 같은 row를 대상(ON l.d = r.d and l.e - r.e)`으로 

`left inner join`을 실행한 다음, 

`left 테이블의 c column을 기준(ORDER BY l.c)`으로

 `내림차순(DESC)으로 정렬`"









