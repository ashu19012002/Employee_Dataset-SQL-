# Employee_Dataset-SQL-

SELECT *FROM employee
SELECT *FROM employeedetail

--Q1(a): Find the list of employees whose salary ranges between 2L to 3L.

SELECT EmpName, Salary FROM Employee
WHERE Salary > 200000 AND Salary < 300000
--- OR –--
SELECT EmpName, Salary FROM Employee
WHERE Salary BETWEEN 200000 AND 300000

--Q1(b): Write a query to retrieve the list of employees from the same city.

SELECT E1.EmpID, E1.EmpName, E1.City
FROM Employee E1, Employee E2
WHERE E1.City = E2.City AND E1.salary != E2.salary

--Q1(c): Query to find the null values in the Employee table.

SELECT * FROM employee
WHERE empid IS NULL

--Q2(a): Query to find the cumulative sum of employee’s salary.

SELECT EmpID, Salary, SUM(Salary) OVER (ORDER BY EmpID) AS CumulativeSum
FROM Employee

--Q2(b): What’s the male and female employees ratio.

SELECT
(COUNT(*) FILTER (WHERE Gender = 'M') * 100.0 / COUNT(*)) AS MalePct,
(COUNT(*) FILTER (WHERE Gender = 'F') * 100.0 / COUNT(*)) AS FemalePct
FROM Employee;

--Q3: Query to fetch the employee’s salary but replace the LAST 2 digits with ‘XX’ 
i.e 12345 will be 123XX

SELECT Salary, 
CONCAT(LEFT(Salary, LEN(Salary)-2), 'XX') as masked_salary
FROM Employee
SELECT Salary, 
CONCAT(SUBSTRING(Salary::text, 1, LENGTH(Salary::text)-2), 'XX') as masked_number
FROM Employee
--- OR –--
SELECT Salary, CONCAT(LEFT(CAST(Salary AS text), LENGTH(CAST(Salary AS text))-2), 'XX') 
AS masked_number
FROM Employee

--Q4: Write a query to fetch even and odd rows from Employee table.

---Fetch even rows
SELECT * FROM Employee 
WHERE MOD(EmpID,2)=0;
---Fetch odd rows
SELECT * FROM Employee 
WHERE MOD(EmpID,2)=1;

--OR

---Fetch even rows
SELECT * FROM 
(SELECT *, ROW_NUMBER() OVER(ORDER BY EmpId) AS 
RowNumber
FROM Employee) AS Emp
WHERE Emp.RowNumber % 2 = 0
---Fetch odd rows
SELECT * FROM 
(SELECT *, ROW_NUMBER() OVER(ORDER BY EmpId) AS 
RowNumber
FROM Employee) AS Emp
WHERE Emp.RowNumber % 2 = 1

Q5(a): Write a query to find all the Employee names whose name:

