# Null Value

`NULL`값인 필드는 값이 없음을 의미한다. `0` 값이나 ` ' '`(공백)값과는 다르다! 말 그대로 빈 값.

테이블의 필드가 `optional`한 경우, 이 필드를 `NULL `값으로 두고 `INSERT`, `UPDATE` 할 수 있다.



## IS NULL, IS NOT NULL

`NULL` 값에는 비교연산자(`=`, `<`, `>`)를 사용할 수 없다. 따라서 `NULL`을 판별하기 위해 `IS NULL`, `IS NOT NULL`을 사용한다.

### 문법

```sql
SELECT column_names
FROM table_name
WHERE column_name IS [NOT] NULL;
```

<br>

### 연습 문제 ([link](https://www.w3schools.com/sql/exercise.asp?filename=exercise_null1))

1. Select all records from the `Customers` where the `PostalCode` column is empty.

   ```sql
   SELECT * FROM Customers
   WHERE PostalCode IS NULL;
   ```

2. Select all records from the `Customers` where the `PostalCode` column is NOT empty.

   ```sql
   SELECT * FROM Customers
   WHERE PostalCode IS NOT NULL;
   ```


