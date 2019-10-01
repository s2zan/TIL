# INSERT INTO

`INSERT INTO`문은 테이블에 새로운 레코드를 삽입한다.

### 문법

```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);

-- 만약 모든 칼럼에 값을 넣는 경우, 칼럼 명시하지 않아도 됨
INSERT INTO table_name
VALUES (value1, value2, value3, ...);
```

<br>

### 연습 문제 ([link](https://www.w3schools.com/sql/exercise.asp?filename=exercise_insert1))

1. Insert a new record in the `Customers` table.

   ```sql
   INSERT INTO Customers (
   CustomerName,
   Address,
   City,
   PostalCode,
   Country)
   VALUES (
   'Lee Jian',
   'blah blah',
   'Seoul',
   '1234',
   'Korea');
   ```

<br>

# UPDATE

`UPDATE`문은 이미 존재하는 레코드를 수정하기 위해 사용한다.

### 문법

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

이때, `WHERE`문에 따르는 조건에 만족하는 **모든** 레코드를 수정한다! 조건 작성에 유의하자!

<br>

### 연습 문제 ([link](https://www.w3schools.com/sql/exercise.asp?filename=exercise_update1))

1. Update the `City` column of all records in the `Customers` table.

   ```sql
   UPDATE Customers
   SET City='Oslo';
   ```

2. Set the value of the `City` columns to 'Oslo', but only the ones where the `Country` column has the value "Norway".

   ```sql
   UPDATE Customers
   SET City='Oslo'
   WHERE Country='Norway';
   ```

3. Update the `City` value *and* the `Country` value.

   ```sql
   UPDATE Customers
   SET City='Oslo', Country='Norway'
   WHERE CustomerID=32;
   ```

<br>

# DELETE

`DELETE`문은 이미 존재하는 레코드를 삭제하기 위해 사용한다.

### 문법

```sql
DELETE FROM table_name WHERE condition;
```

이때, `WHERE`문에 따르는 조건에 만족하는 **모든** 레코드를 삭제한다! 조건 작성에 유의하자!

<br>

### 연습 문제 ([link](https://www.w3schools.com/sql/exercise.asp?filename=exercise_delete1))

1. Delete all the records from the `Customers` table where the `Country` value is 'Norway'.

   ```sql
   DELETE FROM Customers
   WHERE Country='Norway';
   ```

2. Delete all the records from the `Customers` table.

   ```sql
   DELETE FROM Customers;
   ```