# SELECT TOP (LIMIT, ROWNUM)

`SELECT TOP`절은 반환할 레코드 수를 지정하는 데 사용된다. 큰 규모의 데이터베이스에서 유용하다.

**MySQL**은  `LIMIT` , **오라클**은 `ROWNUM`을 사용한다.

### 문법

```sql
SELECT TOP number|percent column_name(s)
FROM table_name
WHERE condition;
```

### MySQL 문법

```sql
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number;
```

### 오라클 문법

```sql
SELECT column_name(s)
FROM table_name
WHERE ROWNUM <= number;
```

예를 들어, Customers 테이블에서 앞에서부터 3개의 레코드만 조회하고자 한다면,

```sql
SELECT TOP 3 * FROM Customers;

SELECT * FROM Customers
LIMIT 3;

SELECT * FROM Customers
WHERE ROWNUM <= 3;
```

`SELECT TOP`절에서 %로 제한을 주고자 한다면, 

```sql
SELECT TOP 50 PERCENT * FROM Customers`
```

`WHERE`절과 함께 사용한다면, 조건을 만족시키는 레코드 중 앞에서부터 3개의 레코드를 반환한다.