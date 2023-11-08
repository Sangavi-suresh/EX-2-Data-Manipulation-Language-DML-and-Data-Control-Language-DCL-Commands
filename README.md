# EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands

DATE : 10/08/23

#AIM:

To create a student database and execute DDL queries using SQL. To create a manager database and execute DML queries using SQL.

#DML(Data Manipulation Language) :

The SQL commands that deal with the manipulation of data present in the database belong to DML or Data Manipulation Language and this includes most of the SQL statements. It is the component of the SQL statement that controls access to data and to the database. Basically, DCL statements are grouped with DML statements.
#List of DML commands :

INSERT: It is used to insert data into a table.
UPDATE: It is used to update existing data within a table.
DELETE: It is used to delete records from a database table.
#Create the table as given below :

create table manager(enumber number(6),ename char(15),salary number(5),
commission number(4),annualsalary number(7),Hiredate date,designation char(10)
,deptno number(2),reporting char(10));

#Insert the following values into the table:

insert into manager values(7369,'Dharsan',2500,500,30000,'30-June-81','clerk',10,'John');
insert into manager values(7839,'Subu',3000,400,36000,'1-Jul-82','manager',null,'James');
insert into manager values(7934,'Aadhi',3500,300,42000,'1-May-82','manager',30,NULL);
insert into manager values(7788,'Vikash',4000,0,48000,'12-Aug-82','clerk',50,'Bond');

Q1) Update all the records of manager table by increasing 10% of their salary as bonus.
QUERY :
UPDATE manager
SET salary = salary + (salary * 0.10),
annualsalary = annualsalary + (annualsalary * 0.10);
OUTPUT :
![image](https://github.com/Sangavi-suresh/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118541861/7606b9a3-8f93-4c75-a5f9-16d3902e6c9c)

Q2) Delete the records from manager table where the salary less than 2750.
QUERY :
DELETE FROM manager WHERE salary < 2750;

OUTPUT :

![image](https://github.com/Sangavi-suresh/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118541861/a0708993-be19-4883-aabc-219a36e06f7a)

Q3) Display each name of the employee as “Name” and annual salary as “Annual Salary” (Note: Salary in emp table is the monthly salary)
QUERY :
SELECT ename AS "Name", salary * 12 AS "Annual Salary"
FROM manager;
OUTPUT :

![image](https://github.com/Sangavi-suresh/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118541861/1c83445f-37aa-4459-be4a-4ff3b5967c64)

Q5) List the names of Clerks from emp table.
QUERY :
SELECT ename from manager where designation='clerk';
OUTPUT :

![image](https://github.com/Sangavi-suresh/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118541861/e0bbafa7-230c-4598-b951-2c6f12c8b2ed)

Q6) List the names of employee who are not Managers.
QUERY :
SELECT ename from manager where designation!='manager';
OUTPUT :

![image](https://github.com/Sangavi-suresh/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118541861/1cf08b44-1606-4a98-bc76-73e5e5320c90)

Q7) List the names of employees not eligible for commission.
QUERY :
SELECT ename from manager where commission=0;
OUTPUT :

![image](https://github.com/Sangavi-suresh/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118541861/0393701b-bd50-43cd-ad55-e8ad436ed517)

Q8) List employees whose name either start or end with ‘s’.
QUERY :
SELECT ename
FROM manager
WHERE ename LIKE 'S%' OR ename LIKE '%s';
OUTPUT :

![image](https://github.com/Sangavi-suresh/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118541861/0f59a4c3-b8f4-454c-b439-adf47b3c4c2d)

Q9) Sort emp table in ascending order by hire-date and list ename, job, deptno and hire-date.
QUERY :
select ename,designation,deptno,Hiredate from manager
order by Hiredate asc;
OUTPUT :

![image](https://github.com/Sangavi-suresh/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118541861/6e70d592-dd9e-4d93-a832-5cdbabb3a347)

Q10) List the Details of Employees who have joined before 30 Sept 81.
QUERY :
SELECT *
FROM manager
WHERE Hiredate < TO_DATE('1981-09-30', 'YYYY-MM-DD');
OUTPUT :

![image](https://github.com/Sangavi-suresh/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118541861/8e2d375d-e1c2-4fcf-8cd2-696e69a48c44)

Q11) List ename, deptno and sal after sorting emp table in ascending order by deptno and then descending order by sal.
QUERY :
select ename,deptno,salary from manager order by deptno asc;
select ename,deptno,salary from manager order by salary desc;
OUTPUT :

![image](https://github.com/Sangavi-suresh/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118541861/65835df7-98d2-4fd2-b6d5-ab2ff01c1191)

![image](https://github.com/Sangavi-suresh/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118541861/28576d21-4b07-479c-969d-2d68c66c9a3e)

Q12) List the names of employees not belonging to dept no 30,40 & 10
QUERY :
select ename from manager where deptno not in (10,30,40);
OUTPUT :

![image](https://github.com/Sangavi-suresh/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118541861/c38bcc37-fee0-4bde-a0f7-6f1dff811cf0)

Q13) Find number of rows in the table EMP
QUERY :
select count(*) from manager;
OUTPUT :

![image](https://github.com/Sangavi-suresh/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118541861/c2fc8fb8-1ddf-4725-8502-53dff3869a80)

Q14) Find maximum, minimum and average salary in EMP table.
QUERY :
select ename ,salary,annualsalary from manager
where salary = (select max(salary) from manager);

select ename ,salary,annualsalary from manager
where salary = (select min(salary) from manager);

select avg(salary) from manager;
OUTPUT :

![image](https://github.com/Sangavi-suresh/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118541861/647d88a8-1e37-494f-a3fe-7a1c38c8a7ff)

![image](https://github.com/Sangavi-suresh/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118541861/ae3700e9-ac2a-401c-8d36-f2b39352e57e)

![image](https://github.com/Sangavi-suresh/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118541861/5bdf2972-203b-47fc-9145-08c4bc221cca)

Q15) List the jobs and number of employees in each job. The result should be in the descending order of the number of employees.
QUERY :
SELECT designation, COUNT(*) AS "Number of Employees"
FROM manager
GROUP BY designation
ORDER BY COUNT(*) DESC;
OUTPUT :

![image](https://github.com/Sangavi-suresh/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118541861/28fdcfc2-b0f4-4ad3-9dee-352f3812435c)

RESULT :
Thus, Manager database is created and DML queries such as insertion, updation, deletion are executed using SQL.



























