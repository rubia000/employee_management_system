**Employee Management System REST API**

A simple,REST API built with Spring Boot to manage Employee records.
It features complete CRUD operations,input validation and exception handling.
# Tech Stack
* Java 17
* Spring Boot
* Spring Data JPA
* MySQL Database
* Maven
# Setup & Installation Instructions
Follow the instructions below to run the project locally on your machine:
1. Prerequisites-

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
`

b)Open the configuration file located at src/main/resources/application.yml (or application.properties) and update your MySQL username and password:
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

| Operation | HTTP Method | Endpoint | Description |
| :--- | :--- | :--- | :--- |
| **Get All Employees** | `GET` | `/api/employees` | Retrieves a list of all employees |
| **Get Employee by ID** | `GET` | `/api/employees/{id}` | Retrieves a single employee by their ID |
| **Create Employee** | `POST` | `/api/employees` | Adds a new employee (with input validation) |
| **Update Employee** | `PUT` | `/api/employees/{id}` | Updates an existing employee's details |
| **Delete Employee** | `DELETE` | `/api/employees/{id}` | Removes an employee by ID |                           Removes an employee by ID

# Input Validation and Exception Handling:
* Input Validation: If you try to submit a POST or PUT request with invalid fields (eg: blank names or negative salary), the API triggers @Valid checks and responds with a  400 Bad Request 
listing the specific constraint issues.
* Global Exceptions: If you request an ID that does not exist in the database, the global exception handler catches it and returns a  structured JSON error response instead of a stack trace.

#  Database Configuration

This application connects to a **MySQL** database.

1. Ensure MySQL is running on your local machine.
2. Create a database named `employee_db` :
   ```
   CREATE DATABASE employee_db;
3.Update your src/main/resources/application.properties file with your local MySQL credentials:

`spring.datasource.url=jdbc:mysql://localhost:3306/employee_db?useSSL=false&serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=your_mysql_password
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQLDialect`

# Sample requests and responses:

### 1. Get All Employees (`GET /api/employees`)
* **Response (`200 OK`):**
  ```json
  [
      {
          "id": 1,
          "firstName": "kiran",
          "lastName": "Dev",
          "email": "kiran.dev@gmail.com",
          "department": "Engineering",
          "salary": 75000.0
      },
      {
          "id": 2,
          "firstName": "mini",
          "lastName": "terese",
          "email": "mini.terese@gmail.com",
          "department": "ElectricalEngineering",
          "salary": 65000.0
      },
      {
          "id": 3,
          "firstName": "arjun",
          "lastName": "krishna",
          "email": "arjun.krishna@gmail.com",
          "department": "marketing",
          "salary": 50000.0
      },
      {
          "id": 4,
          "firstName": "dona",
          "lastName": "mathew",
          "email": "dona.mathew@gmail.com",
          "department": "FullStackDevelopment",
          "salary": 55000.0
      }
  ]

2. Get Employee by ID (GET /api/employees/2)
   Response (200 OK):

JSON
`{
"id": 2,
"firstName": "mini",
"lastName": "terese",
"email": "mini.terese@gmail.com",
"department": "ElectricalEngineering",
"salary": 65000.0
}`
3. Create Employee (POST /api/employees)
   Request Body (application/json):

JSON
`{
"firstName": "Akash",
"lastName": "M",
"email": "akash.m@example.com",
"department": "ProjectManagement",
"salary": 77000.0
}`
Response (201 Created or 200 OK):

JSON
`{
"id": 5,
"firstName": "Akash",
"lastName": "M",
"email": "akash.m@example.com",
"department": "ProjectManagement",
"salary": 77000.0
}`
4. Update Employee (PUT /api/employees/5)
   Request Body (application/json):

JSON
`{
"firstName": "Akash",
"lastName": "K",
"email": "akash.k@gmail.com",
"department": "ProjectManagement",
"salary": 77000.0
}`
Response (200 OK):

JSON
`{
"id": 5,
"firstName": "Akash",
"lastName": "K",
"email": "akash.k@gmail.com",
"department": "ProjectManagement",
"salary": 77000.0
}`
5. Delete Employee (DELETE /api/employees/5)
   Endpoint: http://localhost:8080/api/employees/5

Response (204 No Content or 200 OK):

Employee deleted successfully 