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

#### EQUI JOIN AND NON EQUI JOIN

###### EQUI JOIN :

> EQUI JOIN creates a JOIN for equality or matching column(s) values of the relative tables. EQUI JOIN also create JOIN by using JOIN with ON and then providing the names of the columns with their relative tables to check equality using equal sign (=).

###### NON EQUI JOIN :

> NON EQUI JOIN performs a JOIN using comparison operator other than equal(=) sign like >, <, >=, <= with conditions.

<details><summary>SHOW ALL</summary>

- Display all the managers & clerks name, id along with their department details who work in Accounts and Marketing departments.
  ```
  select * from emp, dept where emp.deptno = dept.deptno and dname in ('ACCOUNTING', 'MARKETING') and job in ('MANAGER', 'CLERK')
  ```
- Display all the salesmen’s name,job,dname and loc who are not located at DALLAS.
  ```
   select emp.ename, emp.job, dept.dname, dept.loc from emp, dept where dept.loc != 'DALLAS' and emp.job='SALESMAN' and emp.deptno = dept.deptno
  ```
- Select department name & location of all the employees working for CLARK.
  ```
  select dept.dname, dept.loc, emp.* from dept, emp where dept.deptno = emp.deptno and emp.mgr = (select empno from emp where ename = 'CLARK')
  ```
- Select all the departmental information for all the managers.(Manager is not a job)
  ```
  select dept.* from dept, emp where emp.deptno = dept.deptno and emp.empno in (select mgr from emp)
  ```
- Select all the employees who work in DALLAS.
  ```
  select emp.*, dept.* from dept, emp where dept.loc = 'DALLAS' and emp.deptno = dept.deptno
  ```
- Find the highest paid employee of sales department. (Show his empno,ename,dname,sal,loc).
  ```
  select emp.empno, emp.ename, dept.dname, dept.loc, emp.sal from dept, emp where emp.SAL = (select max(SAL) from emp, dept where emp.deptno = dept.deptno and dept.dname = 'SALES') and emp.deptno = dept.deptno
  ```
- List the emps with departmental information Whose Jobs are same as MILLER or Sal is more than ALLEN.
  ```
  select emp.*, dept.* from emp, dept where emp.deptno = dept.deptno and (sal > (select sal from emp where ename='ALLEN') or job = (select job from emp where ename = 'MILLER'))
  ```
- Find out the employees who are working in CHICAGO and DALLAS.
  ```
  select * from emp where deptno in ( select deptno from dept where loc in ('CHICAGO', 'DALLAS'))
  ```
- List all the Grade2 and Grade 3 emps.
  ```
  select * from emp where sal in (select sal from salgrade, emp where salgrade.grade in (2,3) and emp.sal between salgrade.losal and salgrade.hisal)
  ```
- Display all Grade 4,5 Analyst and Manager.
  ```
  select * from emp where sal in (select sal from salgrade, emp where salgrade.grade in (4,5) and emp.sal between salgrade.losal and salgrade.hisal) and JOB in ('ANALYST', 'MANAGER')
  ```
- List all the Grade2 and Grade 3 emps who belong from the Chicago.
  ```
  select * from emp where sal in (select sal from salgrade, emp where salgrade.grade in (2,3) and emp.sal between salgrade.losal and salgrade.hisal) and deptno = (select deptno from dept where loc='CHICAGO')
  ```
- Find the highest paid employee of sales department. (Show his empno,ename,dname,sal,loc).

  ```
  select empno, ename, dname, sal, loc from emp, dept where emp.deptno = dept.deptno and sal = (select max(sal) from emp, dept where emp.deptno = dept.deptno and dept.deptno =  (select deptno from dept where dname = 'SALES'))
  ```

- Find out the mgr who lives in DALLAS and belong from grade 3 and 4.
  ```
  select * from emp where deptno in (select deptno from dept where loc='DALLAS') and EMPNO in ( select MGR from emp where sal in (select sal from salgrade, emp where salgrade.grade in (3,4) and emp.sal between salgrade.losal and salgrade.hisal))
  ```
- Find out the grade of all mgrs.
  ```
  select emp.*, grade from emp, salgrade where emp.sal between losal and hisal and empno in (select mgr from emp)
  ```

</details>

#### SUB QUERY

<details><summary>SHOW ALL</summary>

- Show the details of the min salary holder of the employee table.
  ```
  select * from EMP where SAL = (select MIN(SAL) from EMP)
  ```
- Find the details of the most senior employee.
  ```
  select * from EMP where HIREDATE = (select min(HIREDATE) from EMP)
  ```
- Select all the employees who are earning same as BLAKE.
  ```
  select * from EMP where SAL = (Select SAL from EMP where ENAME = 'BLAKE')
  ```
- Display all the employees who have joined after FORD
  ```
  select * from EMP where HIREDATE>(select HIREDATE from EMP where ENAME='FORD')
  ```
- List all the employees who are earning more than SMITH and less then KING.
  ```
  select * from EMP where SAL > (select SAL from EMP where ENAME='SMITH') and SAL < (select SAL from EMP where ENAME = 'KING')
  ```
- Find the employees who work in the same department with BLAKE
  ```
  select * from EMP where DEPTNO = (select DEPTNO from EMP where ENAME='BLAKE')
  ```
- Display all the salesmen who are not located at DALLAS.
  ```
  select * from EMP where JOB='SALESMAN' and DEPTNO != (select DEPTNO from DEPT where LOC ='DALLAS')
  ```
- Select department name & location of all the employees working for CLARK.
  ```
  select DNAME, LOC from DEPT where DEPTNO = (select DEPTNO from EMP where MGR=(select EMPNO from EMP where ENAME = 'CLARK'))
  ```
- Select all the departmental information for all the managers.
  ```
  select * from DEPT where DEPTNO in (select DEPTNO from EMP where JOB = 'MANAGER')
  ```
- Display all the managers & clerks who work in Accounts and Marketing departments.
  ```
  select * from EMP where JOB in ('MANAGER', 'CLERK') and DEPTNO = (select DEPTNO from DEPT where DNAME in ('ACCOUNTING', 'MARKETING'))
  ```
- Select all the employees who work in DALLAS.
` select * from EMP where DEPTNO = (select DEPTNO from DEPT where LOC = 'DALLAS') `
</details>

#### GROUP BY

> The GROUP BY statement groups rows that have the same values into summary rows. This statement is often used with aggregate functions (COUNT(), MAX(), MIN(), SUM(), AVG()) to group the result-set by one or more columns.

<details><summary>SHOW ALL</summary>

- Find out the grade with the maximum No of employees.
  ```
  select grade, count(*) from emp, salgrade where sal between losal and hisal group by grade having count(*)  = (select max(count(*)) from emp, salgrade where sal between losal and hisal group by grade)
  ```
- List out the Name, Job, Salary,grade of the emps in the department with the highest average salary
  ```
  select ename, job, sal, grade from emp, salgrade where sal between losal and hisal and deptno = (select deptno from emp group by deptno having avg(sal) = (select max(avg(sal)) from emp group by deptno))
  ```
- Write a query to display the department name, location name and number of employees and their rounded average salary for all employees as department name wise and location wise.
  ```
  select dname, loc, count(*), round(avg(sal)) from emp, dept where emp.deptno = dept.deptno group by dname,loc
  ```
- Find out the location with maximum no of average salary.
  ```
  select loc from dept where deptno = (select deptno from emp group by deptno having avg(sal) = (select max(avg(sal)) from emp group by deptno))
  ```
- List the Name,job,sal,dname and grade of the loc where highest no.of emps are working.
  ```
  select ename, job,sal, dname, grade from emp,dept,salgrade where emp.deptno = dept.deptno and sal between losal and hisal and loc = (select loc from dept, emp where emp.deptno = dept.deptno group by loc having count(*) = (select max(count(*)) from emp,dept where emp.deptno = dept.deptno group by loc))
  ```
- Find out the employee details of the grade which has the maximum number of the employees who belong from the sales department.
  ```
  select emp.* from emp, salgrade where sal between losal and hisal and grade = (select grade from emp, salgrade where sal between losal and hisal group by grade having count(*)  = (select max(count(*)) from emp, salgrade where sal between losal and hisal group by grade)) and deptno = (select deptno from dept where dname='SALES')
  ```
- List the highest paid emp of Chicago joined before the most recently hired emp of grade2
  ```
  select emp.* from emp, dept where emp.deptno = dept.deptno and sal = (select max(sal) from emp, dept where emp.deptno = dept.deptno and loc='CHICAGO' and hiredate < (select max(hiredate) from emp,salgrade where sal between losal and hisal and grade = 2))
  ```
- Increment the salary of the emplyees to 7% who belong from grade 2.
  ```
  update emp set sal=(sal+(sal*0.07)) where sal in (select sal from emp, salgrade where sal between losal and hisal and grade = 2)
  ```
- Delete the most senior employee.
  ```
  delete from emp where hiredate = (select min(hiredate) from emp)
  ```

</details>
