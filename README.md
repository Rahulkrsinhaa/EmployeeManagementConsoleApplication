# Employee Management Console Application

A simple Java 17 console application demonstrating Java fundamentals, object-oriented programming, collections, exception handling, interfaces, and the Stream API.

## Features

- Add employees with ID, name, department, salary, and active status
- Display all employees
- Search by employee ID
- Filter employees by department
- Filter active employees whose salary is above a given amount
- Handle missing, duplicate, invalid, and malformed employee data

## Project structure

```text
src/main/java/com/example/ems/
├── EmployeeManagementConsole.java
├── model/Employee.java
├── repository/EmployeeRepository.java
├── repository/InMemoryEmployeeRepository.java
├── service/EmployeeService.java
└── exception/
    ├── EmployeeException.java
    ├── EmployeeNotFoundException.java
    ├── DuplicateEmployeeException.java
    └── InvalidEmployeeException.java
```

## Run

Requires JDK 17 or newer and Maven.

```bash
mvn test
mvn exec:java
```

The application starts with the four employees from the assignment example. Choose option `5` and enter `100000` to see Sam and Priya.