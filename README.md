   base de donnée

1.premièrement il faut créer une base de donnée

create database  manage_surf;

2.utiliser cette database
use manage_surf;



 



CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    email VARCHAR(100),
    password VARCHAR(255),
    role ENUM('admin','client'),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    country VARCHAR(100),
    level ENUM('beginner','intermediate','advanced'),
    user_id INT,
    FOREIGN KEY (user_id) REFERENCES users(id)
);

CREATE TABLE lessons (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(100),
    coach VARCHAR(100),
  description TEXT,
  price DECIMAL(10,2),
 level ENUM('beginner','intermediate','advanced'),
    date DATETIME
);

CREATE TABLE enrollments (
    id INT AUTO_INCREMENT PRIMARY KEY,
    student_id INT,
    lesson_id INT,
    payment_status ENUM('paid','pending'),
    FOREIGN KEY (student_id) REFERENCES students(id),
    FOREIGN KEY (lesson_id) REFERENCES lessons(id)
);

<img width="1248" height="692" alt="image" src="https://github.com/user-attachments/assets/41f005d4-dac4-4637-90be-15784d89a9b8" />


