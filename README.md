# Employee_Dataset-SQL-

SELECT *FROM employee
SELECT *FROM employeedetail



--Q1(b): Write a query to retrieve the list of employees from the same city.

SELECT E1.EmpID, E1.EmpName, E1.City
FROM Employee E1, Employee E2
WHERE E1.City = E2.City AND E1.salary != E2.salary
