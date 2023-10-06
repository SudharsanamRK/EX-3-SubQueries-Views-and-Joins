# EX 3 SubQueries, Views and Joins 


## Create employee Table
```sql
CREATE TABLE EMP (EMPNO NUMBER(4) PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR NUMBER(4),HIREDATE DATE,SAL NUMBER(7,2),COMM NUMBER(7,2),DEPTNO NUMBER(2));
```
## Insert the values
```sql
INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```

## Create department table
```sql
CREATE TABLE DEPT (DEPTNO NUMBER(2) PRIMARY KEY,DNAME VARCHAR2(14),LOC VARCHAR2(13));
```
## Insert the values in the department table
```sql
INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```

### Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.


### QUERY:

```sql
CREATE VIEW details AS SELECT ENAME FROM EMP WHERE SAL >(select SAL from EMP where EMPNO=7566);
```
### OUTPUT:
![view creation img](https://github.com/SudharsanamRK/EX-3-SubQueries-Views-and-Joins/assets/115523484/3c6c06d6-98c5-4c7b-8249-d0c4c880d9b0)

### Q2) List the ename,job,sal of the employee who get minimum salary in the company.

### QUERY:
 ```sql
CREATE VIEW minimum AS select ENAME,JOB,SAL from EMP where SAL =(select MIN(SAL) from EMP);
```

### OUTPUT:
![min salary img](https://github.com/SudharsanamRK/EX-3-SubQueries-Views-and-Joins/assets/115523484/5706020f-56fd-4d14-9b47-7a9f70cd0312)

### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.

### QUERY:
```sql
select ENAME,JOB from EMP where  DEPTNO=10 AND JOB='SALESMAN';
```
### OUTPUT:
![sales dept img](https://github.com/SudharsanamRK/EX-3-SubQueries-Views-and-Joins/assets/115523484/d5a35841-5575-41ab-9a30-281bacca549d)



### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.

### QUERY:
```sql
create view empv5 as select EMPNO,ENAME,JOB from EMP where DEPTNO=10;
```

### OUTPUT:
![Create a view img](https://github.com/SudharsanamRK/EX-3-SubQueries-Views-and-Joins/assets/115523484/f0447a0c-bb12-42df-a721-21a02cf9f5e3)

### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.

### QUERY:
```sql
create view empv30 AS select EMPNO,ENAME,SAL from EMP where DEPTNO=30;
```

### OUTPUT:
![Creation of View](https://github.com/SudharsanamRK/EX-3-SubQueries-Views-and-Joins/assets/115523484/22633ae4-2c15-4db5-a8c1-9003b0f4d3b0)


### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table

### QUERY:
```sql
update EMP set SAL=SAL*1.1 WHERE JOB='clerk';

create view empv8 as select EMPNO,ENAME,SAL,JOB from EMP;
```
### OUTPUT:
![Updation of View](https://github.com/SudharsanamRK/EX-3-SubQueries-Views-and-Joins/assets/115523484/eb512d27-c33c-4a80-92c0-ce644d4de1a9)

## Create a Customer1 Table
```sql
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
## Inserting Values to the Table
```sql
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```
## Create a Salesperson1 table
```sql
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```
## Inserting Values to the Table
```sql
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```
### Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

### QUERY:
```sql
SELECT salesman1.name AS "Salesman", customer1.cust_name AS "Customer Name", salesman1.city AS "City" from salesman1 INNER JOIN customer1 ON salesman1.city=customer1.city;
```


### OUTPUT:
![Inner Join](https://github.com/SudharsanamRK/EX-3-SubQueries-Views-and-Joins/assets/115523484/4796583e-42c9-4445-8fac-748bdaa9d47d)

### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.


### QUERY:
```
SELECT customer1.cust_name AS "Customer Name",customer1.city AS "Customer City",salesman1.name AS "Salesman",salesman1.commission AS "Commission" FROM salesman1 INNER JOIN customer1 ON salesman1.salesman_id=customer1.salesman_id WHERE salesman1.commission>0.13;
```

### OUTPUT:
![Inner Join](https://github.com/SudharsanamRK/EX-3-SubQueries-Views-and-Joins/assets/115523484/176cb88f-9d55-4680-a8b7-ea28c9121911)

### Q9) Perform Natural join on both tables

### QUERY:
```sql
SELECT customer1.cust_name AS "Customer Name",customer1.city AS "Customer City",salesman1.name AS "Salesman",salesman1.commission AS "Commission" FROM salesman1 INNER JOIN customer1 ON salesman1.salesman_id=customer1.salesman_id WHERE salesman1.commission>0.13;
```

### OUTPUT:
![Inner Join](https://github.com/SudharsanamRK/EX-3-SubQueries-Views-and-Joins/assets/115523484/9d9cf018-c49a-436e-80e6-b32e5b89d2fa)

### Q10) Perform Left and right join on both tables

### QUERY FOR LEFT JOIN:

```sql
SELECT customer1.cust_name AS "Customer Name",customer1.city AS "Customer City",salesman1.name AS "Salesman",salesman1.commissioSELECT customer1.cust_name AS "Customer Name",customer1.city AS "Customer City",salesman1.name AS "Salesman",salesman1.commission AS "Commission" FROM salesman1 INNER JOIN customer1 ON salesman1.salesman_id=customer1.salesman_id WHERE salesman1.commission>0.13;
```
```sql
select * from customer1 natural join salesman1;
```
### OUTPUT FOR LEFT JOIN:
![Left Join](https://github.com/SudharsanamRK/EX-3-SubQueries-Views-and-Joins/assets/115523484/e37c49da-592a-4e62-97aa-f805c0bc6ef0)
### QUERY FOR RIGHT JOIN:
 ```
SELECT * FROM salesman1 RIGHT JOIN customer1 ON salesman1.salesman_id=customer1.salesman_id;
```
### OUTPUT FOR RIGHT JOIN:
![Right Join](https://github.com/SudharsanamRK/EX-3-SubQueries-Views-and-Joins/assets/115523484/e5644bac-ced0-49d6-83c2-48cc20b0c5f6)

### RESULT:
Thus, the queries are executed successfully.
