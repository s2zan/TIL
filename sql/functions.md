# MIN(), MAX()

`MIN()`, `MAX()` 함수는 선택한 칼럼에서 각각 최소값과 최대값을 반환한다.

### 문법

```sql
-- 최소값
SELECT MIN(column_name)
FROM table_name
WHERE condition;

-- 최대값
SELECT MAX(column_name)
FROM table_name
WHERE condition;
```

<br>

# COUNT(), AVG(), SUM()

`COUNT()`는 조건을 만족하는 행의 수를 반환한다.

`AVG()`, `SUM()` 함수는 선택한 숫자 칼럼에서 각각 평균과 합계를 반환한다.

### 문법

```sql
SELECT COUNT(column_name)
FROM table_name
WHERE condition;

SELECT AVG(column_name)
FROM table_name
WHERE condition;

SELECT SUM(column_name)
FROM table_name
WHERE condition;
```



<br>

### 연습 문제 ([link](https://www.w3schools.com/sql/exercise.asp?filename=exercise_functions1))

1. Use the `MIN` function to select the record with the smallest value of the `Price` column.

   ```sql
   SELECT MIN(Price) FROM Products;
   ```
   
2. Use an SQL function to select the record with the highest value of the `Price` column.

   ```sql
   SELECT MAX(Price) FROM Products;
   ```
   
3. Use the correct function to return the numbers of records that have the `Price` value set to `18`.

   ```sql
   SELECT COUNT(*)
   FROM Products
   WHERE Price=18;
   ```

4. Use an SQL function to calculate the average price of all products.

   ```sql
   SELECT AVG(Price) FROM Products;
   ```

5. Use an SQL function to calculate the sum of all the `Price` column values in the `Products` table.

   ```sql
   SELECT SUM(Price) FROM Products;
   ```

   