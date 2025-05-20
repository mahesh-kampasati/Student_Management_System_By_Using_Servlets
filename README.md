# Student_Management_System_By_Using_Servlets
Student Management System built using Java Servlets, JSP, and MySQL. This project supports role-based access for Admin, Teacher, and Student to manage registration, attendance, and academic performance.
# 🎓 Student Management System (Using Java Servlets & MySQL)

This project is a role-based **Student Management System** developed using **Java Servlets**, **JSP/HTML**, and **MySQL**. It supports functionalities for three types of users: **Admin**, **Teacher**, and **Student**.

## 🔧 Tech Stack

- **Java**
- **JSP / HTML / CSS**
- **Servlet API**
- **MySQL (JDBC)**
- **Apache Tomcat (Server)**

---

## 🧑‍💻 Roles & Features

### 🔑 Admin
- Registers Students and Teachers
- Stores login credentials in the `users` table
- Stores extended details in `students` and `teachers` tables

### 👨‍🏫 Teacher
- Logs in using credentials
- Marks **student performance** (subject, marks, total marks, teacher name)
- Data stored in the `performance` table

### 👨‍🎓 Student
- Views subject-wise marks
- Calculates **total marks, percentage, and grade**
- Data is fetched from the `performance` table

---

## 🗃️ Database Schema (MySQL)

### 1. `users`
```sql
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    gender VARCHAR(10) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    password VARCHAR(100) NOT NULL,
    role VARCHAR(20) NOT NULL
);


users (all NOT NULL)

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    email VARCHAR(100) NOT NULL,
    password VARCHAR(100) NOT NULL,
    role VARCHAR(20) NOT NULL,
    userName VARCHAR(100) NOT NULL,
    gender VARCHAR(10) NOT NULL
);
students (all NOT NULL)

CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    name VARCHAR(100) NOT NULL,
    stream VARCHAR(100) NOT NULL,
    percentage DOUBLE NOT NULL,
    gender VARCHAR(10) NOT NULL
);
teachers (all NOT NULL)

CREATE TABLE teachers (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    name VARCHAR(100) NOT NULL,
    subject VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL,
    password VARCHAR(100) NOT NULL
);

CREATE TABLE attendance (
    id INT AUTO_INCREMENT PRIMARY KEY,
    student_id INT,
    date DATE,
    status VARCHAR(10),
    FOREIGN KEY (student_id) REFERENCES students(id)
);

🚀 How to Run the Project
✅ Prerequisites
Java JDK 8+

Apache Tomcat 9+

MySQL Server

Any IDE (Eclipse/IntelliJ/VS Code)

MySQL Workbench or phpMyAdmin (for DB)

🧩 Steps to Run
Clone the Repository

bash
Copy
Edit
git clone https://github.com/your-username/student-management-system.git
cd student-management-system
Create MySQL Database

Create a database named: student_management

Run the SQL scripts provided above to create tables

Configure Database Credentials

In each servlet, update the connection:

java
Copy
Edit
Connection con = DriverManager.getConnection(
  "jdbc:mysql://localhost:3306/student_management", "root", "YourPassword");
Deploy on Tomcat

Place project files in the webapps directory or import into Eclipse/IntelliJ

Start the Tomcat server

Access via: http://localhost:8080/student-management-system/

Login

Add some dummy users into users, students, and teachers manually or via SQL

Project Structure
student-management-system/
│
├── WebContent/
│   ├── login.html
│   ├── register.html
│   ├── performance_form.html
│   ├── view_result.html
│   ├── teacher_dashboard.html
│   ├── student_dashboard.html
│   ├── styles.css
│
├── src/
│   ├── com/
│   │   ├── LoginServlet.java
│   │   ├── RegisterServlet.java
│   │   ├── PerformanceServlet.java
│   │   ├── ResultServlet.java
│   │   ├── TeacherDashboardServlet.java
│   │   ├── StudentDashboardServlet.java
│   │
│   ├── model/
│   │   ├── User.java
│   │   ├── Student.java
│   │   ├── Teacher.java
│   │   ├── Performance.java
│   │
│   ├── dao/
│   │   ├── UserDAO.java
│   │   ├── StudentDAO.java
│   │   ├── TeacherDAO.java
│   │   ├── PerformanceDAO.java
│   │
│   ├── service/
│   │   ├── UserService.java
│   │   ├── PerformanceService.java
│
├── WEB-INF/
│   └── web.xml
