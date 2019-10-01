# WHERE

`WHERE`절은 레코드를 필터링하기 위해 사용한다.

`SELECT`문 뿐만 아니라  `UPDATE`,  `DELETE`문에서도 사용된다!

### 문법

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

예를 들어, `Customers` 테이블에서 한국 출신의 고객만 조회하고 싶다면

```sql
SELECT * FROM Customers
WHERE Country='Korea'
```



## AND, OR, NOT

### 문법

```sql
SELECT column1, column2, ...
FROM table_name
WHERE (condition1 AND NOT condition2) OR condition3 ...;
```

<br>

### 연습 문제 ([link](https://www.w3schools.com/sql/exercise.asp?filename=exercise_where1))

1. Select all records where the `City` column has the value "Berlin".

   ```sql
   SELECT * FROM Customers
   WHERE City='Berlin';
   ```

2. Use the `NOT` keyword to select all records where `City` is NOT "Berlin".

   ```sql
   SELECT * FROM Customers
   WHERE NOT City='Berlin';
   ```

3. Select all records where the `CustomerID` column has the value 32.

   ```sql
   SELECT * FROM Customers
   WHERE CustomerID=32;
```

4. Select all records where the `City` column has the value 'Berlin' *and* the `PostalCode` column has the value 12209.

   ```sql
   SELECT * FROM Customers
   WHERE City='Berlin'
   AND PostalCode=12209;
   ```

5. Select all records where the `City` column has the value 'Berlin' or 'London'.

   ```sql
   SELECT * FROM Customers
   WHERE City='Berlin'
   OR City='London';
   ```

   

