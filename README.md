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
