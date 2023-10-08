# Ex. No: 5 Creating Triggers using PL/SQL

### AIM: To create a Trigger using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

### Program:
```
NAME: BHARATH K
Reg.no: 212222110006
```

CREATE TABLE sal_log (
  log_id NUMBER GENERATED ALWAYS AS IDENTITY,
  empid NUMBER,
  empname VARCHAR2(10),
  old_salary NUMBER,
  new_salary NUMBER,
  update_date DATE
);

### Create employee table:

```
CREATE TABLE employed(
  empid NUMBER,
  empname VARCHAR2(10),
  dept VARCHAR2(10),
  salary NUMBER
);
```
![image](https://github.com/BharathCSEIOT/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/122793480/d94325cf-a53d-43ed-a7d1-189012fc470d)

### Create salary_log table:
```
CREATE TABLE sal_log (
  log_id NUMBER GENERATED ALWAYS AS IDENTITY,
  empid NUMBER,
  empname VARCHAR2(10),
  old_salary NUMBER,
  new_salary NUMBER,
  update_date DATE
);
```
![image](https://github.com/BharathCSEIOT/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/122793480/980d51a9-32bc-4ced-af8a-9859983daf60)

### PLSQL Trigger code
->create trigger 
```
CREATE OR REPLACE TRIGGER sal_log_update
BEFORE UPDATE ON employed
FOR EACH ROW
BEGIN
  IF :OLD.salary != :NEW.salary THEN
    INSERT INTO sal_log (empid, empname, old_salary, new_salary, update_date)
    VALUES (:OLD.empid, :OLD.empname, :OLD.salary, :NEW.salary, SYSDATE);
  END IF;
END;
/
```
->Update the salary of an employee
```
UPDATE employed
SET salary = 60000
WHERE empid = 1;
```
->Display the employee table
```
SELECT * FROM employed;
```
->Display the salary_log table
```
SELECT * FROM sal_log;
```
### Output:
![image](https://github.com/BharathCSEIOT/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/122793480/ccb4447b-c2ed-4638-81d3-e22801984f8b)

### Result:
The program has been implemented successfully.
