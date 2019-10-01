# SELECT

`SELECT`문은 데이터베이스에서 데이터를 선택하는 데 사용,  반환된 데이터는 `result-set`이라고 하는 결과 테이블에 저장된다.

### 문법

```sql
SELECT column1, column2, ...
FROM table_name;

SELECT * FROM table_name; -- SELECT ALL
```



## SELECT DISTINCT

`SELECT DISTINCT` 문은 중복된 값을 제외하고 고유한 값만을 반환한다.

### 문법

```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

<br>

### 연습 문제 ([link](https://www.w3schools.com/sql/exercise.asp?filename=exercise_select1))

1. Insert the missing statement to get all the columns from the `Customers` table.

   ```sql
   SELECT * FROM Customers;
   ```

2. Write a statement that will select the `City` column from the `Customers` table.

   ```sql
   SELECT City FROM Customers;
   ```

3. Select all the *different* values from the `Country` column in the `Customers` table.

   ```sql
   SELECT DISTINCT Country FROM Customers;
   ```

   