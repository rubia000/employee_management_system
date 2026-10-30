**Employee Management System REST API**
A simple,REST API built with Spring Boot to manage Employee records.It features complete CRUD operations,input validation and exception handling.
# Tech Stack
* Java 17
* Spring Boot
* Spring Data JPA
* MySQL Database
* Maven
# Setup & Installation Instructions
Follow the instructions below to run the project locally on your machine:
1. Prerequisites
Install:
* Java 17 or higher
* Maven
* MySQL Server
* An IDE such as IntelliJ IDEA.
2. Clone the Repository:
   `git clone <your-repository-url>
   cd employee_management_system`
3. Configure the Database:
a)Open your MySQL client and create a database named employee_db:
`   CREATE DATABASE employee_db;
`b)Open the configuration file located at src/main/resources/application.yml (or application.properties) and update your MySQL username and password:
  ` spring:
   datasource:
   url: jdbc:mysql://localhost:3306/employee_db
   username: root
   password: your_mysql_password`
4. Run the Application:
Open the project in your IDE.
   Inside src/main/java/com/empl/demo,run DemoApplication.java.
# Testing the API(Postman Endpoints):
You can test using Postman with the following base URL:
http://localhost:8080/api/employees

**Operation**               **HTTP Method**                **Endpoint**                                  **Description**
Get All Employees             GET                           /api/employees                                 Retrieves a list of all employees
Get Employee by ID            GET                           /api/employees/{id}                            Retrieves a single employee by their ID
Create Employee               POST                          /api/employees                                 Adds a new employee (with input validation)
Update Employee               PUT                           /api/employees/{id}                            Updates an existing employee's details
Delete Employee               DELETE                        /api/employees/{id}                            Removes an employee by ID

# Input Validation and Exception Handling:
* Input Validation: If you try to submit a POST or PUT request with invalid fields (eg: blank names or negative salary), the API triggers @Valid checks and responds with a  400 Bad Request 
listing the specific constraint issues.
* Global Exceptions: If you request an ID that does not exist in the database, the global exception handler catches it and returns a  structured JSON error response instead of a stack trace.