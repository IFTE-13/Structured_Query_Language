## OBJECT BROWSER

### EMP TABLE

| Column Name |  Data Type   | Nullable | Default | Primary Key |
| :---------: | :----------: | :------: | :-----: | :---------: |
|    EMPNO    | NUMBER(4,0)  |    No    |    -    |      1      |
|    ENAME    | VARCHAR2(10) |   Yes    |    -    |      -      |
|     JOB     | VARCHAR2(9)  |   Yes    |    -    |      -      |
|     MGR     | NUMBER(4,0)  |   Yes    |    -    |      -      |
|  HIREDATE   |     DATE     |   Yes    |    -    |      -      |
|     SAL     | NUMBER(7,2)  |   Yes    |    -    |      -      |
|    COMM     | NUMBER(7,2)  |   Yes    |    -    |      -      |
|   DEPTNO    | NUMBER(2,0)  |   Yes    |    -    |      -      |

### DEPT TABLE

| Column Name |  Data Type   | Nullable | Default | Primary Key |
| :---------: | :----------: | :------: | :-----: | :---------: |
|   DEPTNO    | NUMBER(2,0)  |    No    |    -    |      1      |
|    DNAME    | VARCHAR2(14) |   Yes    |    -    |      -      |
|     LOC     | VARCHAR2(13) |   Yes    |    -    |      -      |

### SALGRADE TABLE

| Column Name | Data Type | Nullable | Default | Primary Key |
| :---------: | :-------: | :------: | :-----: | :---------: |
|    GRADE    |  NUMBER   |   Yes    |    -    |      -      |
|    LOSAL    |  NUMBER   |   Yes    |    -    |      -      |
|    HISAL    |  NUMBER   |   Yes    |    -    |      -      |

## DATA

#### EMP TABLE

| EMPNO | ENAME  |    JOB    | MGR  | HIREDATE  | SAL  | COMM | DEPTNO |
| :---: | :----: | :-------: | :--: | :-------: | :--: | :--: | :----: |
| 7369  | SMITH  |   CLERK   | 7902 | 17-DEC-80 | 800  |  -   |   20   |
| 7499  | ALLEN  | SALESMAN  | 7698 | 20-FEB-81 | 1600 | 300  |   30   |
| 7521  |  WARD  | SALESMAN  | 7698 | 22-FEB-81 | 1250 | 500  |   30   |
| 7566  | JONES  |  MANAGER  | 7839 | 02-APR-81 | 2975 |  -   |   20   |
| 7654  | MARTIN | SALESMAN  | 7698 | 28-SEP-81 | 1250 | 1400 |   30   |
| 7698  | BLAKE  |  MANAGER  | 7839 | 01-MAY-81 | 2850 |  -   |   30   |
| 7782  | CLARK  |  MANAGER  | 7839 | 09-JUN-81 | 2450 |  -   |   10   |
| 7788  | SCOTT  |  ANALYST  | 7566 | 19-APR-87 | 3000 |  -   |   20   |
| 7839  |  KING  | PRESIDENT |  -   | 17-NOV-81 | 5000 |  -   |   10   |
| 7844  | TURNER | SALESMAN  | 7698 | 08-SEP-81 | 1500 |  0   |   30   |
| 7876  | ADAMS  |   CLERK   | 7788 | 23-MAY-87 | 1100 |  -   |   20   |
| 7900  | JAMES  |   CLERK   | 7698 | 03-DEC-81 | 950  |  -   |   30   |
| 7902  |  FORD  |  ANALYST  | 7566 | 03-DEC-81 | 3000 |  -   |   20   |
| 7934  | MILLER |   CLERK   | 7782 | 23-JAN-82 | 1300 |  -   |   10   |

#### DEPT TABLE

| DEPTNO |   DNAME    |   LOC    |
| :----: | :--------: | :------: |
|   10   | ACCOUNTING | NEW YORK |
|   20   |  RESEARCH  |  DALLAS  |
|   30   |   SALES    | CHICAGO  |
|   40   | OPERATIONS |  BOSTON  |

#### SALGRADE TABLE

| GRADE | LOSAL | HISAL |
| :---: | :---: | :---: |
|   1   |  700  | 1200  |
|   2   | 1201  | 1400  |
|   3   | 1401  | 2000  |
|   4   | 2001  | 3000  |
|   5   | 3001  | 9999  |

## QURIES

#### JOINING

<details><summary>CLICK ME</summary>
<p>

#### We can hide anything, even code!

```ruby
   puts "Hello World"
```

</p>
</details>