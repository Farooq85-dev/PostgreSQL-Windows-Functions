# PostgreSQL-Windows-Functions

## This repository is about windows functions in MongoDb.

### What are windows functions?

#### Window functions are a powerful feature in SQL that allow you to perform calculations across a set of rows that are related to the current row. Unlike regular aggregate functions, which return a single result for a group of rows, window functions return a result for each row while considering a "window" of rows around it.

### 1) `create a table`

```
CREATE TABLE employees (
employee_id SERIAL PRIMARY KEY,
first_name VARCHAR(50),
last_name VARCHAR(50),
email VARCHAR(100),
phone_number VARCHAR(15),
hire_date DATE,
job_title VARCHAR(50),
salary NUMERIC(10, 2)
);
```

### 2) ` insert data into table`

```
INSERT INTO employees (first_name, last_name, email, phone_number, hire_date, job_title, salary) VALUES
('John', 'Doe', 'john.doe@example.com', '555-1234', '2022-01-15', 'Software Engineer', 70000.00),
('Jane', 'Smith', 'jane.smith@example.com', '555-5678', '2021-03-22', 'Project Manager', 85000.00),
('Alice', 'Johnson', 'alice.johnson@example.com', '555-8765', '2020-07-30', 'Data Analyst', 60000.00),
('Bob', 'Brown', 'bob.brown@example.com', '555-4321', '2023-05-10', 'UX Designer', 75000.00),
('Charlie', 'Davis', 'charlie.davis@example.com', '555-1357', '2019-11-12', 'Database Administrator', 80000.00);
```

### 3) `over()`

```
select sum (salary) over() from employees;
```

```
select first_name, salary, sum (salary) over() from employees;
```

```
select first_name, salary, avg (salary) over() from employees;
```

### 4) `Row_Number()`

```
select first_name, salary, Row_Number() Over() from employees;
```

```
select first_name, salary, Row_Number() Over(order by first_name) from employees;
```

```
select first_name, salary, Row_Number() Over(partition by job_title) from employees;
```

### 4) `Rank()`

```
select first_name,salary,  Rank() over(order by salary ASC) from employees;
```

### 5) `DENSE_Rank()`

```
select first_name,salary,  DENSE_Rank() over(order by salary ASC) from employees;
```

### 6) `lag()`

```
select first_name,salary,  lag(salary) over() from employees;
```

### 7) `lead()`

```
select first_name,salary,  lead(salary) over() from employees;
```
