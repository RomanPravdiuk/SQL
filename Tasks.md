1.Вивести всіх працівників, чиї зарплати є в базі, разом із зарплатами.
```sql
SELECT employee_name, monthly_salary FROM employees
JOIN employee_salary
ON employees.employee_Id = employee_salary.employee_id
JOIN Salary
ON employee_salary.salary_id = Salary.Salary_Id;
```

2.Вивести всіх працівників у яких ЗП менше 2000
```sql
SELECT employee_name, monthly_salary FROM employees
JOIN employee_salary
ON employees.employee_Id = employee_salary.employee_id
JOIN Salary
ON employee_salary.salary_id = Salary.Salary_Id
WHERE monthly_salary < 2000;
```

3.Вивести всі зарплатні позиції, але працівника за ними не призначено. (ЗП є, але незрозуміло хто її отримує.
```sql
SELECT employee_name, monthly_salary FROM employees
FULL JOIN employee_salary
ON employees.employee_Id = employee_salary.employee_id
FULL JOIN Salary
ON employee_salary.salary_id = Salary.Salary_Id
WHERE employee_name IS NULL;
```

4.Вивести всі зарплатні позиції, менші за 2000, але працівника за ними не призначено. (ЗП є, але незрозуміло хто її отримує.)
```sql
SELECT employee_name, monthly_salary FROM employees
FULL JOIN employee_salary
ON employees.employee_Id = employee_salary.employee_id
FULL JOIN Salary
ON employee_salary.salary_id = Salary.Salary_Id
WHERE employee_name IS NULL
OR monthly_salary < 2000;
```

5.Знайти всіх працівників кому не нарахована ЗП.
```sql
FULL JOIN employee_salary
ON employees.employee_Id = employee_salary.employee_id
FULL JOIN Salary
ON employee_salary.salary_id = Salary.Salary_Id
WHERE monthly_salary IS NULL;
```

6.Вивести імена та посаду тільки Java розробників.
```sql
SELECT employee_name, role_name FROM employees
JOIN roles_employee
ON employees.employee_Id = roles_employee.employee_id
JOIN roles
ON roles_employee.roles_id = roles.roles_id
WHERE role_name LIKE "%java developer%";
```

7.Вивести імена та посаду тільки Python розробників.
```sql
SELECT employee_name, role_name FROM employees
JOIN roles_employee
ON employees.employee_Id = roles_employee.employee_id
JOIN roles
ON roles_employee.roles_id = roles.roles_id
WHERE role_name LIKE "%Python developer%";
```

8.Вивести імена та посаду всіх QA інженерів.
```sql
SELECT employee_name, role_name FROM employees
JOIN roles_employee
ON employees.employee_Id = roles_employee.employee_id
JOIN roles
ON roles_employee.roles_id = roles.roles_id
WHERE role_name LIKE "%QA%";
```

9.Вивести імена та зарплати Senior Java розробників.
```sql
SELECT employee_name, role_name, monthly_salary FROM employees
JOIN roles_employee
ON employees.employee_Id = roles_employee.employee_id
JOIN roles
ON roles_employee.roles_id = roles.roles_id
JOIN employee_salary
ON employees.employee_Id = employee_salary.employee_id
JOIN Salary
ON employee_salary.salary_id = Salary.Salary_Id
WHERE roles.role_name LIKE "%Senior Java developer%";
```

10.Вивести імена, посади та ЗП усіх фахівців за зростанням.
```sql
SELECT employee_name, role_name, monthly_salary FROM employees
JOIN roles_employee
ON employees.employee_Id = roles_employee.employee_id
JOIN roles
ON roles_employee.roles_id = roles.roles_id
JOIN employee_salary
ON employees.employee_Id = employee_salary.employee_id
JOIN Salary
ON employee_salary.salary_id = Salary.Salary_Id
ORDER BY employees.employee_name, roles.role_name, Salary.monthly_salary ASC;
```
