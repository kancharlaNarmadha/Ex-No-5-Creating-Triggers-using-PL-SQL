# Ex-No-5-Creating-Triggers-using-PL-SQL
# DATE:
# AIM:
To create a Trigger using PL/SQL.

# Steps:
1.Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);

2.Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);

3.Create a trigger named as log_salary-update.

4.Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.

5.End the trigger.

6.Update the salary of an employee in employee table.

7.Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.

8.Display the employee table, salary_log table.


# Program:
```
 create table employee6(empid number,empname varchar(12),dept varchar(10),salary number);
 create table salar_log(log_id number generated always as identity,empid number,empname varchar(12),old_salary number,new_salary number,update_date date);
```
# Create employee table:
![dbms exp 5 1](https://github.com/kancharlaNarmadha/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119559316/da5108ff-bf26-4208-86e5-af83da71b017)

# Create salary_log table:

![dbms exp 5 2](https://github.com/kancharlaNarmadha/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119559316/8352905b-ed6c-42bd-b64c-3074d673a55f)


# PLSQL Trigger code:
```
-- Create the trigger
 create trigger log_salar_update
   before update on employee6
   for each row
   declare
   v_old_salary number;
   v_new_salary number;
   begin
   if :OLD.salary != :NEW.salary then
   insert into salar_log (empid, empname, old_salary, new_salary, update_date)                                                                          0  values (:OLD.empid, :OLD.empname, :OLD.salary, :NEW.salary, SYSDATE);
   end if;
   end;
   /
-- Insert the values in the employee table
 insert into employee6 values(1,'Ajay','IT',100000);
 insert into employee6 values(2,'Vijay','MD',500000);
-- Update the salary of an employee
update employee6 set salary = 60000 where empid = 1;
-- Display the employee table
select * from employee6;
--Display the salary_log table
select * from salar_log;
```
# Output:
![dbms exp 5 3](https://github.com/kancharlaNarmadha/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119559316/b45a6d0a-40fb-4508-ad46-9c719f649ec6)
# Result:
Thus the program for creating triggers has been implemented successfully.
