# ORDER BY

`ORDER BY`는 result-set을 오름차순 또는 내림차순으로 정렬하는 데 사용된다.

기본적으로 오름차순으로 정렬하며 (`ASC`로 표기하기도), 내림차순으로 정렬하기 위해선 `DESC`사용

### 문법

```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... [ASC | DESC];
```

만약 다음과 같이 여러가지 칼럼을 입력한다면,

```sql
SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;
```

먼저 Country를 기준으로 오름차순 정렬한 후, 동일한 값을 가진 row의 경우 CustomerName을 기준으로 내림차순 정렬한다.

<br>

### 연습 문제 ([link](https://www.w3schools.com/sql/exercise.asp?filename=exercise_orderby1))

1. Select all records from the `Customers` table, sort the result alphabetically by the column `City`.

   ```sql
   SELECT * FROM Customers
   ORDER BY City;
   ```

2. Select all records from the `Customers` table, sort the result *reversed* alphabetically by the column `City`.

   ```sql
   SELECT * FROM Customers
   ORDER BY City DESC;
   ```

3. Select all records from the `Customers` table, sort the result alphabetically, first by the column `Country`, then, by the column `City`.

   ```sql
   SELECT * FROM Customers
   ORDER BY Country, City;
   ```

