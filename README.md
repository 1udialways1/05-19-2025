show databases;

use vit;

#drop database VIT;

#drop table cse;

#alter table cse drop column s_name;

show tables;

desc cse;

#delete - is used to delete a particular row & table 

CREATE TABLE Worker (

	WORKER_ID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,

	FIRST_NAME CHAR(25),

	LAST_NAME CHAR(25),

	SALARY INT(15),

	JOINING_DATE DATETIME,

	DEPARTMENT CHAR(25)

);

use vit;

INSERT INTO Worker 

	(WORKER_ID, FIRST_NAME, LAST_NAME, SALARY, JOINING_DATE, DEPARTMENT) VALUES

		(001, 'Monika', 'Arora', 100000, '14-02-20 09.00.00', 'HR'),

		(002, 'Niharika', 'Verma', 80000, '14-06-11 09.00.00', 'Admin'),

		(003, 'Vishal', 'Singhal', 300000, '14-02-20 09.00.00', 'HR'),

		(004, 'Amitabh', 'Singh', 500000, '14-02-20 09.00.00', 'Admin'),

		(005, 'Vivek', 'Bhati', 500000, '14-06-11 09.00.00', 'Admin'),

		(006, 'Vipul', 'Diwan', 200000, '14-06-11 09.00.00', 'Account'),

		(007, 'Satish', 'Kumar', 75000, '14-01-20 09.00.00', 'Account'),

		(008, 'Geetika', 'Chauhan', 90000, '14-04-11 09.00.00', 'Admin');

show tables;

select * from Worker;

delete from worker where department='HR';

delete from worker where salary <=100000;

delete from worker where first_name='vivek';

delete from worker where worker_id=4;



truncate table worker;

delete from worker;



create table devp(name varchar(20),number int );

start transaction;

insert into devp values('naidu',2005); 

savepoint a12;

insert into devp values('Ravi',2004);

savepoint a1;

select * from devp;

delete from devp where name='ravi';

select * from devp;

rollback to a1;

select * from devp;

show tables;

desc profile;

select * from profile;

select * from profile where M_no=675;

select M_no from profile;

select Address from profile;

select M_no as mobile_number from profile;



#operators-logical and common

select * from worker; 

select first_name from worker where salary <200000;

select first_name from worker where salary=100000;

select first_name from worker where salary>=10000000;

select first_name from worker where salary <10000000;

select first_name from worker where salary <200000 & department='HR';

select * from worker where salary >200000 AND department='HR';

select * from worker where salary <200000 AND department='HR' OR 'ADMIN';

select first_name from worker where salary <300000 AND SALARY>100000 AND department='Account'OR'ADMIN';



#IN OPERATOR

select * from worker where worker_id IN (1,6,7);



#in even number worker id who is getting more salary and HR & Admin Team

select * from worker where salary=(select MAX(salary)From Worker) AND (department='HR'OR'ADMIN') AND worker_id IN(2,4,6,8);

SELECT * FROM worker WHERE salary = (SELECT MAX(salary) FROM worker) AND (department ='HR' OR department= 'ADMIN') AND worker_id%2=0;
