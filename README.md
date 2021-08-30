# SQL Task

## Prerequisites 
   **Microsoft SQL Server Management Studio 18**

## Employee

| emp_id | first_name | last_name | gender | position | department_id | salary | 
| --- | --- | --- | --- | --- | --- | --- | 
| 10001 | Super | Man | M | QA | 1 | 45000 | 
| 10002 | Jessica | Liyers | F | Architech | 1 | 60000 | 
| 10003 | Bonnie | Adams | F | Product Manager | 1 | 80000 | 
| 10004 | James | Madison | M | Software Developer | 1 | 75000 | 
| 10005 | Michael | Greenback | M | Sales Assistant | 2 | 85000 | 
| 10007 | Leslie | Peters | F | Sales engineer | 2 | 76000 | 
| 10008 | Max | Powel | M | Sales representative | 2 | 59000 | 
| 10009 | Stacy | Jacobes | F | Sales manager | 2 | 73000 | 

## Department1

| department_id | department_name | 
| ---| --- | 
| 1 | IT | 
| 2 | Sales | 

# Solution
1. Return Employee record with highest salary
```
SELECT * FROM Employee
WHERE salary = (SELECT Max(Salary) FROM Employee)
```
or
```
select min(salary) from(
select distinct top 1 salary from Employee order by salary desc) as salary
```
2. Return highest salary
```
SELECT salary FROM Employee
WHERE salary = (SELECT Max(Salary) FROM Employee)
```

3. Return 2nd highest salary
```
SELECT MIN(salary) FROM(
SELECT DISTINCT TOP 2 salary FROM Employee ORDER BY salary DESC) AS salary
```

4. Select range o femployees nased on id
```
Unable to understand question 
```

5. Return an employee with highest salary and department name
```
WITH table_t AS (
SELECT e.first_name, e.department_id, e.emp_id, e.salary,d.department_name,
(ROW_NUMBER() OVER (PARTITION BY e.department_id ORDER BY e.salary DESC) )rnum
FROM Employee e join department1 d ON e.department_id=d.department_id
)
SELECT 
first_name, emp_id, department_id, department_name,salary FROM table_t WHERE rnum=1
```

6. Return higest salary, employee_name, department_name for EACH department
```
WITH table_t AS (
SELECT e.first_name, e.department_id, e.emp_id, e.salary,d.department_name,
(ROW_NUMBER() OVER (PARTITION BY e.department_id ORDER BY e.salary DESC) )rnum
FROM Employee e join department1 d ON e.department_id=d.department_id 
)
SELECT 
first_name, emp_id, department_id, department_name,salary FROM table_t WHERE rnum=1
```
-----------------------------------------------------------------------------------------------------------------

💪 Mastering automation testing to improve software quality

🚀 Unleashing the potential of using Selenium WebDriver for automation















