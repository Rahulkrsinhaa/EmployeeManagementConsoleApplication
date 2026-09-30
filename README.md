# Employee Management Console Application

A menu-driven Java 17 application for adding, finding, and filtering employee records. The project demonstrates object-oriented programming, collections, interfaces, custom exception handling, and the Java Stream API.

## Features

- Add employees with an ID, name, department, salary, and active status.
- Display all employees or search by employee ID.
- Filter employees by department (case-insensitive).
- Find active employees earning above a salary threshold, sorted by salary from highest to lowest.
- Display helpful errors for duplicate IDs, missing employees, invalid employee details, and malformed numeric input.

Employee data is stored in memory. Each run starts with four sample employees; records added during a session are lost when the application exits.

## Prerequisites

- JDK 17 or newer
- Apache Maven

Check that both are available on your `PATH`:

```sh
java -version
mvn -version
```

## Run the application

Open a terminal in the project directory containing `pom.xml`, then run:

```sh
mvn compile exec:java
```

Enter a menu option and follow the prompts:

```text
=== Employee Management Console ===
1. Add employee
2. Display all employees
3. Search by employee ID
4. Display employees by department
5. Display active employees above salary
0. Exit
Choose an option:
```

When adding an employee, use a unique positive ID, a nonblank name and department, and a finite, non-negative salary. Enter `y` for active status or `n` for inactive status.

## Try the sample data

| ID | Name | Department | Salary | Status |
| --- | --- | --- | ---: | --- |
| 101 | Alex | Engineering | 90,000 | Active |
| 102 | Sam | Engineering | 125,000 | Active |
| 103 | John | Finance | 140,000 | Inactive |
| 104 | Priya | Engineering | 150,000 | Active |

- Choose `3` and enter `102` to find Sam.
- Choose `4` and enter `engineering` to see Alex, Sam, and Priya.
- Choose `5` and enter `100000` to see Priya followed by Sam. Only active employees whose salary is strictly greater than the entered amount are included.
- Choose `0` to exit.

## Project structure

```text
pom.xml
src/
|-- main/java/com/example/ems/
|   |-- EmployeeManagementConsole.java   # Console menu and input handling
|   |-- model/Employee.java              # Employee data
|   |-- repository/                     # Repository interface and in-memory storage
|   |-- service/EmployeeService.java     # Validation, search, and filtering
|   `-- exception/                      # Custom employee exceptions
`-- test/java/com/example/ems/service/
    `-- EmployeeServiceTest.java
```

The console delegates business logic to `EmployeeService`, which accesses employee records through the `EmployeeRepository` interface. `InMemoryEmployeeRepository` provides the storage implementation.

## Run tests

```sh
mvn test
```

The JUnit 5 tests cover listing and finding employees, department filtering, salary filtering and ordering, missing IDs, duplicate IDs, and selected invalid employee details.

To clean previous build output, run tests, and package the application:

```sh
mvn clean package
```

Maven writes build output to `target/`, which is excluded from Git.
